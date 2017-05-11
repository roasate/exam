
# FOSS LAB EXAM

Three problems were asked to be solved 

  - Amicable Number
  - Remove blank lines from a given file
  - Online BMI calculator

# Amicable Numbers

  - a pair of numbers, each of which is the sum of the factors of the other.
  - eg 220 and 284
  
```sh
##CODE##
#!/bin/sh
i=1
var=0
while [ $i -le 10000 ]
do
        k=`expr $i - 1`
        sum=0
        for j in `seq 1 $k`
        do
                a=`expr $i % $j`
                if [ $a -eq 0 ]
                then
                        sum=`expr $sum + $j`
                fi
        done
        #echo $sum 
        sum1=0
        k=`expr $sum - 1`
        for j in `seq 1 $k`
        do
                a=`expr $sum % $j`
                if [ $a -eq 0 ]
                then
                        sum1=`expr $sum1 + $j`
                fi
        done
        #echo $sum1
        if [ $sum -ne $sum1 ]
        then
                if [ $i -eq $sum1 ]
                then 
                        echo "$i"
                        var=`expr $var + $i`
                fi
        fi
        i=`expr $i + 1`
done
echo "Sum=$var"






```
What the program does is that it inputs value from 1 - 10000 using a while loop and it checks if it is amicable that is sum of the factors of the other are equal if so it is outputed and sum is incremented with the amicable value and the finally the sum is outputed when the loop runs out.











### Blank Lines

```sh
##CODE##
#!/bin/sh
if [ $# -ne 2 ]
then
	echo "Invalid number of parameters"
	exit
fi
file=$1
if test -s "$file"
then
	echo file exist
else
	echo file doesnot exist
fi
grep -v -w  -i "" $1 > $2





```

What the above code does is that it inputs two files as parameters and checks for number of parameters if not true points out an error using grep we can check for the empty lines and using invert (-v) we can copy all the mismatches to a new file and that is the output we require.

### Installation

Dillinger requires [Node.js](https://nodejs.org/) v4+ to run.

Install the dependencies and devDependencies and start the server.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

For production environments...

```sh
$ npm install --production
$ npm run predeploy
$ NODE_ENV=production node app
```

### Plugins

Dillinger is currently extended with the following plugins. Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md] [PlDb] |
| Github | [plugins/github/README.md] [PlGh] |
| Google Drive | [plugins/googledrive/README.md] [PlGd] |
| OneDrive | [plugins/onedrive/README.md] [PlOd] |
| Medium | [plugins/medium/README.md] [PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md] [PlGa] |


### Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantanously see your updates!

Open your favorite Terminal and run these commands.

First Tab:
```sh
$ node app
```

Second Tab:
```sh
$ gulp watch
```

(optional) Third:
```sh
$ karma test
```
#### Building for source
For production release:
```sh
$ gulp build --prod
```
Generating pre-built zip archives for distribution:
```sh
$ gulp build dist --prod
```
### Docker
Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 80, so change this within the Dockerfile if necessary. When ready, simply use the Dockerfile to build the image.

```sh
cd dillinger
docker build -t joemccann/dillinger:${package.json.version}
```
This will create the dillinger image and pull in the necessary dependencies. Be sure to swap out `${package.json.version}` with the actual version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on your host. In this example, we simply map port 8000 of the host to port 80 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart="always" <youruser>/dillinger:${package.json.version}
```

Verify the deployment by navigating to your server address in your preferred browser.

```sh
127.0.0.1:8000
```

#### Kubernetes + Google Cloud

See [KUBERNETES.md](https://github.com/joemccann/dillinger/blob/master/KUBERNETES.md)


### Todos

 - Write MOAR Tests
 - Add Night Mode

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
