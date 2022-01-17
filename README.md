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
         
