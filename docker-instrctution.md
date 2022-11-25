## dockerfiles contains instructions for building an image

## dockerfile
- FROM // specify base image, we take the base image which contain for specify base image
- WORKDIR  //To specify the work dir
- ADD   // for copy files and dir
- COPY  // for copy files and dir
- RUN   //execute the fiels
- ENV   // setting the environment variable
- EXPOSE  // for telling docker  that our container is start at agiven port
- USER // for specify the user that should run the application, with user limited privilege
- CMD
- ENTRYPOINT  // TO specify the command should be execuited, when we start.

## we gona build an image
## docker build -t react-app . // to tell docker were to find th dokerfiles

## then the imageis built

## we gonna look at all the image behalf of this machine

## docker image ls //we can see the avaliable enviroment variable
## docker run -it react-app //   start the container -it means interactive mode.
## know we are inside node environment, and we can write in the terminal javascript code and executed the code 

## docker run -it react-app bash
## docker run -it react-app sh

