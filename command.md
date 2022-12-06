# docker command
## docker start the container or pull it from docker hub

```docker run ubuntu
```
## to see the list of process or list of container
```
docker ps

```
## to see the list of process and exit also

```
docker ps -a
```
## best command
```
whoami
pwd
echo hello
history
!3   //to see the number of list history command
```
apt(advance package tool)
apt list
# see the location of shalf program
```
echo $0
```
## to start the container to interact

```
docker run -it ubuntu
```



???
## package managers

npm, yarn,pip,NuGet,apt(advance package tool)

## apt remove nano

## pwt print working dir
## ls -1
## ls-l
## cd../..
## ls /bin
## cd /root
## cd ~ (tilda) to get home dir

# manipulate file and dir in linux ubuntu from terminal

##  blue represent dir, and white represent file in linux ubuntu after we tap ls command
## mkdir 
## mv  move or rename
## mkdir test
## mv test docker  /rename test to docker dir
## mv hello.txt /etc //move file
## touch hello.txt file.txt file1.txt
## rm hello.tx file.txt file*
## rm -r  doker //toremove dir


# file managment 

# sudo apt install nano (it is simple text writer source or place)
## nano file1.txt
## cat file1.txt
## more file1.txt  //press space or inter to see more files of the text exist in the file

## sudo apt install less  // to replace less
## less fiel1.txt // just using up and down arrow
## head -n 5 file1.txt

# merge one file to other using
## cat file1.txt > file2.txt
## cat file1.txt file2.txt > combined.txt
## echo hello > hello.txt
## ls -l /etc > files.txt

# search files
## grep -i hello file1.txt //-i to remove casesensative
## grep - hello file*
## grep -i -r hello . //to find directory
## grep -ir hello .


# find file and dir
## find
## ls -a
## find  /etc
## find -type d
## find  -type f
## find -type f -name "f*"
## find -type f -iname "F*"
## find  / -type f -name "*.py"
## find  / -type f -name "*.py" > python-files.txt



# chaining or combined multiple command

## mkdir test; cd test; echo done
## mkdir test1 && cd test1 && echo done
## mkdir test || echo "directory exists"
## ls  /bin
## less file.txt
## ls /bin | less
## ls /bin | head
## ls /bin | head -n 5
## mkdir hello : cd hello : echo done
## mkdir hello;\
## cd hello;\


# Environment variables  //you should not store sensative information in Environment variable
## printenv
## printenv PATH
## echo $PATH
## export DB_USER=mosh  //set rariable
## echo $DB_USER OR printenv DB_USER  // to read it 
## docker ps -a

## docker start -i 

## echo DB_USER=mosh >> .bashrcb //append another file to .bashrcb file
## ps
## sleep 3
## kill id(number)

## sudo adduser bob
## sudo useradd bob (the orginal api)

# manage group

## sudo groupadd developers
## sudo groupadd developers bob  // add new user into the group

# file permission

##  echo echo hello > deploy.sh
## cat deploy.sh
## ls -l
## .deploy.sh //we will get permission error
## chmod g o u +x _x deploy.sh
## chmod og_x+w-r *.sh