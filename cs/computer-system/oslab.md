
18. 



17. why kernel in the 2-257 sector in disk?
    A: the makefile concatenate the boot.img+kernel.img+user.img
        it use the gen.pl in the utils 


16. 外部设备->TX线->UART串口芯片->放入接收缓冲区，修改状态寄存器->cpu执行

15. inb：从一个I/O端口空间读取1字节->cpu的AL寄存器
    1. 端口空间不是存储数据的地方，而是设备内部的寄存器提供出来的“访问入口”。
    2. 键盘本身有寄存器，然后cpu访问0x60这个端口号，然后键盘知道这是自己的工位，就把一个按键传输到0x60这个地址
    3. 端口空间是一套独立的地址编号，用来访问设备内部寄存器

14. 键盘->terminal emulator->pty(pseudo terminal)->bash,shell ->fork()->exec()->ls->terminal 

13. args(arguments)参数 argv(argument vector) argc(argument count)

12. 我想知道时钟中断的起源，系统是怎么记录时间的？
    getticker()+while(tick>=ticker+n)return;


11. 硬件中断
    (1)串口中断: 我有数据了
    (2)时钟中断: 时间到了

10. ((void(*)())curr->entry)() ;struct pcb{void *entry};
    (1)curr->entry是地址
    (2)函数void func();类型void ();指向函数的指针 void (*)() e. void (*fp)();是一个名fp的函数无参数的函数指针
    (3)把entry 这个地址，转换成函数指针，然后最后的括号，表示调用，

9.  proc_t(process control)    进程控制
    pcb(process control block) 进程控制块
    kstack (kernel stack)      内核栈
    ctx  (context)             上下文，一次进程切换需要保存的cpu状态


8. TSS(task state segment)任务状态段
    (1)任务状态:EIP,EFLAGS,EAX......ESP,SS
    (2)特权级栈:SS0,ESP0,SS1,ESP1,SS2,ESP2

7. SN(syscall number)系统调用号=调用操作系统哪个功能的编号
    系统调用号  功能
    0           read
    1           write
    2           open
    3           close
    ...
    (1)例如:用户程序想调用write():write(fd, buf, len);
        转换成asm->
            movl $SYS_write, %eax //把系统调用号放进eax
            int $0x80             //出发中断进入内核
    (2)流程: 用户程序--eax-->int 0x80->进入内核->context保存寄存器->irq_handle(ctx)->跟进ctx->eax判断系统调用号->switch(ctx->eax)



6. irq_handle:
    有时候需要ESP栈寄存器去修改新值寄存器，于是需要压栈去存储这个ESP这个指针

5. trap.s (assembler directive汇编指令)
    (1).globl irq0; irq0: push $0; push $0; jmp trap;
        :把一个符号声明为全局符号，让linker能在其他文件使用
        第一个push，是error number，判断不同类型的异常
        第二个push，是irq 号；trap是统一处理中断的函数
    (2):extern
        :告诉编译器这个东西被定义了，我只负责使用不定义
    (3) movl 4(%esp), %eax
        把内存地址 ESP + 4 处的 4 字节数据，复制到 EAX 寄存器
    (4)(%esp)
        %esp 里的数当作一个内存地址，然后取这个地址里的值。
    (5)irq_iret(ctx);
        不是函数，是汇编实现的跳转
    (6)#define SYSCALL_PUTSTR
        这是宏，被定义了，所以以后看到#ifdef用于开启某些功能
    (7)asm volatile("": : :);
        asm代表汇编,然后volatile是告诉编译器这条汇编很重要，不要优化

4. IDT:IDTR->IDT[index]->selector->GDT(code segment)->if user 栈指针切换导内核栈--->load CS(selector),EIP(offset)
    1. IDTR寄存器:IDT基地址+IDT大小=base address+limit
        IDT address=IDT base address + interrrupt number*sizeof[GD];
    2. cpu执行指令：IDT[index]->GD->push Eflags,cs,eip->load cs,eip->handler
        CS:EIP->next instruction point in CS segment 0xEIP
        当有中断时，需要暂停，保存，跳转中断处理函数->push 
    2. GD(gate descriptor):多个连续GD形成一个IDT数组 
        31-16 offset(31-16) P DPL 0 type 0 0 0 Not-Used
              selector() offset(15-0)
        (1)p_1:有效位，1即该门有效
        (2)SELECTOR和OFFSET就是入口地址，在保护模式中，是由CS和EIP共同承担PC的任务，而入口地址的CS就是这个SELECTOR，EIP就是OFFSET。
        (3)DPL_2:DPL就是这个门描述符的权限，设为0表示不允许用户程序主动通过int指令陷入这个中断，设为3表示允许用户程序主动通过int指令陷入这个中断。
        (4)TYPE_4分为两种：
            0xE即中断门（Interrupt Gate），这种门对应的中断在响应时还会顺手把中断关了，避免后续处理时由外部中断引发的中断嵌套，外部中断应该使用这种门。
            0xF即陷阱门（Trap Gate），这种门对应的中断在响应时不会改变中断开关的状态，系统调用和异常理应使用这种门。
            在我们的实验中，所有门都使用中断门，也即响应中断后总会关中断，这其实会简化我们操作系统的实现.
    
    
3. IVN=unsigned_8
    1. 内部异常：0-16
    2. 外部中断：32-47
    3. 系统调用：128=0x80

2. 中断？
    1. 外部中断
        1. 原因:cpu too fast,so when has something happen,the hard 设备去寻找cpu
        2. 外部设备:keyboard,mouse,网卡，硬盘，定时器芯片，USB设备
        3. 关中断:
            (1)NMI(non-maskable-interrupt):即无法关中断,不检查EFLAGS寄存器；//电源都要有问题了，你还管不重要的地方
            (2)EFLAGS寄存器:zf zero
                    cf:carry
                    sf:sign
                    of:overflow
                    if:interrupt ;when if=1,then it's ok to interrupt (only controls normal interrupt);
            (3)硬件(用户按键)->IRQ(interrupt requst)->PIC(programmable interrupt controller)->IVN(interrupt vector number)->IDT(interrupt descriptor table)->function;
        4. why 硬件不直接发送IVN，而要PIC转换
            (1)解耦cpu和设备
            (2)统一管理大量设备:IRQ number boost
            (3)process interrupt compete:queue
            (4)允许屏蔽和重新映射
            (5)历史兼容
    2. 内部异常(exception)
        原因:cpu执行指令时发现
        异常指令:/0,非法
    3. 软件中断/系统调用
        原因:程序主动触发
        例子:系统调用syscall,程序调用printf，调用操作系统，然后显示在终端上，io
        (1)用户程序->IVN->IDT->function
    


1. 我要开始oslab2，我是不需要新建一个branch，目前我在branch1，week1，branch2，该怎么做，这个branch2是要在第一周基础上的
    (1)git branch -vv 
    git branch 查看git分支；-v 即verbose显示名字；-v 显示最新commit;
    此外，git branch week2也能创建；git switch week2，也用于切换
    (2)git checkout -b week2=git switch -c week2
    git checkout main切换当前分支到main;-b 即branch,创建一个新的branch;