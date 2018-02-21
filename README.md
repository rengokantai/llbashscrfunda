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
cat '$(cat /etc/hosts)'
```
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
### 4 Using case
```
VAR = $1
case $VAR in
yes)
  echo ok;;
no|n)
  echo
*)
esac
```

## 6.
### 1 Working with Options
```
while getopts "abc:" opt
do
case $opt in
  a) VAR1=m ;;
  b) VAR3="-s $OPTARG";;
esac
done
```

### 3 Working with Arrays
```
names =(a b c)
echo${#names[@]} #length
echo${names[@]}  #print all
```

### 4 Defing Menu Interfaces
```
select DIR in /bin /usr /etc
  if [ -n $DIR ]
  then
    DIR=$DIR
    export DIR
    break
  else
  fi
done
```
complex:
```
select TASK in 'a' 'b' c'
do
  case $REPLY in
    1) TASK=mount;;
    2) TASK='df -h'
    #)
  esac
 if [-n "$TASK" ]
 then
  clear
  $TASK
  break
 else
 fi
done
```
### 6 Exercise 6 sol
```
pinghost()
{
  read HOSTNAME
  ping $HOSTNAME
}
select TASK in '' '' ''
do
case $REPLY in
  1) TASK=passwd;;
  2) TASK=pinghost;;
esac
if [ -n "task" ]
then
  $TASK
  break
else
fi
done
done
```
### 5 Using trap
redefine signal.
```
trap "echo int" INT
```

## 7. Script Debugging and Analyzing
### 2 Common Analyzing Tools
```
bash -v #verbose output
bash -n # syntax error
bash -x #xtrace
```
```
set list  #show hidden char
set nolist
```
