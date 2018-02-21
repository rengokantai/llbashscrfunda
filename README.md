# llbashscrfunda


## 5.
### 2 Using && and ||
When using &&, the second command is executed only if the first returns
an exit code zero
```
[ -z $1 ] && echo $1 is not defined
```
When using ||, the second command is executed only if the first command does not rerurn and 
exit code 0
```
[ -f 1 ] || echo $1 is not a file
```

### 3 Using for
```
for i in `cat /etc/hosts`; do echo $i; done
for i in {1..5}; do echo $i; done
```

###### * means all files in current directory
```
#!/bin/bash
read DIR
cd $DIR
COUNTER=0
for i in *
do
  COUNTER=$((COUNTER+1))
  echo $COUNTER
done
```
