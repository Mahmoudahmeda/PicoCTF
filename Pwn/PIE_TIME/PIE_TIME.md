# PIE TIME

#### بسم الله و الصلاة و السلام علي رسول الله اللهم , و يسر لي أمري و احلل العقدة من لساني يفقهُ قولي

## Let's Start:

### first i downloaded the Binary File& the C File , then we can use any disassemblier tool or decompiler, i used gdb

```console
chmod +x vuln
gdb ./vuln
```

### then i needed to know the functions

```console
info functions
```
### it will return something like this 

![functions list in gdb](../gdb.png)

### soooooo there is something interesting The **win** Function on **0x2a7**!!

##### U can see it's Impelementation on the C file but it just open and print the flag.txt

### so let's rollback to the main function

### we can see that it call the printf twice then takes an input then another printf then exit

### now it's the time to dynamic analysis let's run the program and watch

```console
run
```
### we will find the first printf that printed the main function address 
![Main Function Address](../1.png)

### and the secound printf is for asking for an Address as an input
![input](../2.png)

### as we notice earlier that the **win** function in on **0x2a7**
##### go check the **win** address if u forgot :)

## Exploit

### now connect to the servrer
```console
nc rescued-float.picoctf.net 64536
```
### take the address of the **main** and change the last 3 byte's to **2a7**
![](../3.png)

### our input address is 0x5eb4bd7e22a7

### And BOOOOOOOOOM you WIN the Flag 
![](../4.png)
