
4. entity:plaintext--(algorithm)-->encrypted text--(key)-->plaintext
          the crptography includes: algorithm and key  


3. format格式化我想里面还有“”怎么办
    (1)format("\"{}\"", name)
    (2)format(R"("{}")", "Tom")

2. 遍历哈希表?
    (1)for (auto &p:mp);//p->first;p->second;


1. c++怎么打开一个txt文件，并读取其中的输入  
    (1)string path=R"(E:\dream\2st-sophomore\courses\core\cryptography\test.txt)";
    (2)ifstream file(path);//这个时候file就是这个文件
    (3)string line;while(getline(file,line)){};//提取一行行字符串;
    (4)file.close//关闭
