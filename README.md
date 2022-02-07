# Memory forensics with volatility

## Mem lab 2
Description
   
   `One of the clients of our company, lost the access to his system due to an unknown error. He is supposedly a very popular "environmental" activist. As a part of the investigation, he told us that his go to applications are browsers, his password managers etc. We hope that you can dig into this memory dump and find his important stuff and give it back to us.`
   
   HInt from question:
   
      . Environmental variables  ==> flag 1
      . password manager process in windows.. credts to https://blog.bi0s.in/2020/02/09/Forensics/HackTM-FindMyPass/ ==> flag 2
      . Browser history
      
   Flag 1
      
          volatility -f MemoryDump_Lab2.raw --profile=Win7SP1x64 envars
   Flag 2 
         
## Cyberdefenders

* https://cyberdefenders.org/blueteam-ctf-challenges/65

 13.  An application was run at 2019-03-07 23:06:58 UTC. What is the name of the program? (Include extension)
 
              volatility -f Triage-Memory.mem --profile=Win7SP1x64 shimcache | grep -i "2019-03-07 23:06:58 UTC"
7. How many processes are associated with VCRUNTIME140.dll?

         volatility -f Triage-Memory.mem --profile=Win7SP1x64 dlllist | grep -i "VCRUNTIME140.dll" 
         
 Process dump with volatility 
    
         volatility -f Triage-Memory.mem --profile=Win7SP1x64 procdump --pid 3496 --dump-dir .
15. What is the short name of the file at file record 59045?

    `Mftparser,` as indicated in the Volatility webpage, scans and analyzes entries in the Master File Table (MFT).
 What is the master `file table` MFT in NTFS?
 
            A master file table is a database in which information about every file and directory on an NT File System (NTFS) volume is kept. An MFT will have a minimum one record for every file and directory on the NTFS logical volume.
            
             volatility -f Triage-Memory.mem --profile=Win7SP1x64 mftparser | tee dump/mftparser.txt
# Linux memory forensics
 ###  Linux volatility
         volatility --info | less
         volatility -f challenge.lime --profile=Linuxubuntu1604x64 --info | less
         
 Finding files
 
         volatility -f challenge.lime --profile=Linuxubuntu1604x64 linux_enumerate_files | grep -i "Important.ods"

         ANS
         0xffff8da480678530 
Dump files 

     volatility -f challenge.lime --profile=Linuxubuntu1604x64 linux_find_file -i 0xffff8da480678530 -o import.ods
     
  Linux version 4.15.0-112-generic (buildd@lcy01-amd64-021) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.12)) #113~16.04.1-Ubuntu SMP Fri Jul 10 04:37:08 UTC 2020 (Ubuntu 4.15.0-112.113~16.04.1-generic 4.15.18)
