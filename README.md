example-dancer-on-dotcloud
==========================

example-dancer-on-dotcloud - working example to solve http://stackoverflow.com/questions/18152734/uwsgi-error-perl-application-not-found


#### How to use this project

    git clone https://github.com/johncosta/example-dancer-on-dotcloud
    dotcloud create dancer
    dotcloud push dancer


#### How this project was generated
The example project here was generated using the steps provided 
here: http://docs.dotcloud.com/services/perl/#basic-use

* Step 1:  Start your project

    mkdir ramen-on-dotcloud
    cd ramen-on-dotcloud
    dotcloud create ramen
    
* Step 2: Create a dotcloud.yml file in your ramen-on-dotcloud project root

    www:
      type: perl
      approot: helloperl
      requirements:
        - App::cpanminus
        
* Step 3: Create the following directory structure

    ramen-on-dotcloud/
    |_ dotcloud.yml   (also known as the "Build File")
    |_ helloperl/     (also known as your "approot")
       |_ app.psgi    (mandatory)
       |_ Makefile.PL (optional; can be used to define CPAN dependencies)
       |_ static/     (optional; put your static assets here)
       |_ ...         (all other files: Perl code, etc.)
       
       
* Step 4: Dynamically generate your dancer application.  

** This step typcially breaks if your local setip isn't correct. ** This example project 
supplies *old* but working files.

    cpanm Dancer
    cd ramen-on-dotcloud
    dancer -a helloperl
    echo "require 'bin/app.pl';" > helloperl/app.psgi
    

* Step 5: Edit the Makefile.pl and add Plack

    PREREQ_PM => {
      'Test::More' => 0,
      'YAML'       => 0,
      'Dancer'     => 1.3113,
      'Plack'      => 0,
    },

* Step 6: Push the application to dotCloud

    dotcloud push
    
