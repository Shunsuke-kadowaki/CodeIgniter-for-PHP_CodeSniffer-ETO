# CodeIgniter-for-PHP_CodeSniffer

Provides sniffs for [PHP_CodeSniffer 1.3.0 and above](http://www.squizlabs.com/php-codesniffer) to check [CodeIgniter coding standard](http://codeigniter.com/user_guide/general/styleguide.html).

## Background
I found Thomas ERNEST initiative to provide PHP_CodeSniffer rules for CodeIgniter. While this is a truely great thing, I would get two types of false positives from my scans:
* CodeIgniters end of file comments are usually made with multi line (/* ... */) style comments. In the original CodeIgniter ruleset, multi line comments are not allowed unless they are docBlock style comments. I've modified this so that multi line comments are allowed if they begin with "End of file" or "Location:"
* In most (all?) class files, CodeIgniter have a one row check for BASEPATH on the same row as the PHP opening tag. This practice would make the check for an existing and valid file doc comment fail. 

### Warning
This repo exists mostly so that I can automate setting up my own build environment, but you are free to use it as you see fit. But if Thomas Ernest adopts my changes into his repo, I may remove this repo.

## A bit of story

### PHP_CodeSniffer

[PHP_CodeSniffer](http://www.squizlabs.com/php-codesniffer) is a PHP5 script that tokenises and "sniffs" PHP, JavaScript and CSS files to detect violations of a defined coding standard.

It is an essential development tool that ensures your code remains clean and consistent. It can also help prevent some common semantic errors made by developers.

By default sniffs for a few coding convetions are provided like PEAR, Zend, PHPCS and Squiz. **CodeIgniter-for-PHP_CodeSniffer** is aimed at adding support for CodeIgniter coding convention.

### CodeIgniter coding standard

[CodeIgniter](http://codeigniter.com/) is a powerful PHP framework with a very small footprint, built for PHP coders who need a simple and elegant toolkit to create full-featured web applications.

CodeIgniter is developed by EllisLab. The compagny follows some specific [coding rules](http://codeigniter.com/user_guide/general/styleguide.html) for their developments and for CodeIgniter especially.

Based on PHP_CodeSniffer **CodeIgniter-for-PHP_CodeSniffer** helps to validate most of the rules in CodeIgniter coding standard.

## Installation

There is an [Apache Ant](http://ant.apache.org/) script at the root of the repository. It targets standard Linux environment like Ubuntu with PHP_CodeSniffer 1.3.0 or above installed via PEAR. It requires PHP (in its 5th version).

Just go to the root of the project and type `ant` to set up **CodeIgniter-for-PHP_CodeSniffer**. 
If you have CodeSniffer installed in another directory than "/usr/share/php/PHP/CodeSniffer/" than you can pass the right directory
as argument to ant. Just type `ant -Dphpcs.dir="/path/to/CodeSniffer/"`.

Check that it is installed type `phpcs -i` you should see a list of installed standards.

Then you can go to you project folder and run `phpcs --standard=CodeIgniter my-file-or-my-directory.php`.

If you work on a Windows platform or for any reason, it is easy to edit the installation script. You just need to change the property `phpcs.dir` in `build.xml` to point toward the directory containing PHP_CodeSniffer.
