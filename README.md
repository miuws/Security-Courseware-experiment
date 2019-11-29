# Security-Courseware-experiment
MIT 6.858 Computer Systems Security Lab1

Task 1
寻找并触发2个新的缓冲区溢出漏洞，详细描述漏洞并触发过程。
改写漏洞利用模板exploit-template.py，将两个漏洞利用程序分别命名为exploit-2a.py和exploit-2b.py。最后，用make check-crash命令来验证是否能够令服务器崩溃。

Task 2
利用缓冲区溢出漏洞将shellcode注入到web服务器，删除一个敏感文件/home/httpd/grades.txt。主要任务是构造一个新的shellcode。
**提示：**删除文件系统调用SYS_unlink调用号是10或'\n'(newline)。若'\n'直接出现在HTTP请求URL中，则会被截断，因此需要特殊处理。
实验会用到下列命令：
创建新文件：touch /home/httpd/grades.txt
编译：gcc -m32 -c -o shellcode.bin shellcode.S
提取二进制指令：objcopy -S -O binary -j .text shellcode.bin
执行二进制指令：./run-shellcode shellcode.bin
将攻击程序命名为exploit-3.py，用make check-exstack来检查攻击是否成功。

Task 3
在栈不可执行的web服务器上，采用return-to-libc攻击删除敏感文件/home/httpd/grades.txt。
将攻击程序命名为exploit-4a.py和exploit-4b.py，用make check-libc来检查攻击是否成功。
**提示：**libc中unlink()函数参数是一个指向以'\0'结尾字符串的指针。因此，需在栈中注入字符串，并保证在漏洞触发时，该字符串结尾为'\0'。
