# Grunt.js Tutorial
***
Grunt is an automation machine! It takes the repetitive tasks you have to do all the time, and does them for you like magic.

In this repository is my sample files, but below explains how to go and create your own.

### Setting up grunt.js on your computer or server
* If you don't have Node.js already, [go and install it](http://nodejs.org/)!
* In terminal type:
```
	sudo npm install -g grunt-cli
```
* Celebrate, see wasn't that easy!

Now that it's setup on your computer you can use it anywhere as many times as you'd like, but you have to follow the next step to actually get it working on a project.


### Setting up grunt on your project

* Go in terminal to your project root (for Drupal this would be your theme's directory /sites/all/themes/THEMENAME)
* Create a package.json file which should look like this:

```
{ 
	"name": "example-project",
	"version": "0.1.0",
	"devDependencies": {
		"grunt": "~0.4.1"
	}
}	
```
* in terminal type: 
``` npm install ```
* Grunt is now installed on that project, once again *easy*!

### Configuring Grunt and finding plugins

From here that are *many* options that you can do. Go to [gruntjs.com](http://gruntjs.com) and search for plugins you might like.

All plugins will tell you how to install them and what options to configure, but I will show you a an example. 

If we want to use imagemin to compress images we would:

* Type in terminal 
``` 
npm install grunt-contrib-imagemin --save-dev 
```
* create a gruntfile.js and configure it like this:

```

module.exports = function(grunt) {

    // 1. All configuration goes here
    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),

        imagemin: {
            dynamic: {
                files: [{
                    expand: true,
                    cwd: 'images-pre/',
                    src: ['**/*.{png,jpg,gif}'],
                    dest: 'images'
                }]
            }
        },

    });

    // 3. Where we tell Grunt we plan to use this plug-in.
    grunt.loadNpmTasks('grunt-contrib-imagemin');

    // 4. Where we tell Grunt what to do when we type "grunt" into the terminal.
    grunt.registerTask('default', ['imagemin']);
};

```
* Now you can go in terminal and type ``` grunt ``` and it will compress all your images.

***
This is just a very brief overview of what Grunt can do, don't be afraid to experiement and try new things. Grunt seems to be very good at telling you where your errors are when you break everything, so you should be good!
