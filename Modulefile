name    'spuder-gitlab'
version '0.2.4'
source 'https://github.com/spuder/puppet-gitlab'
author 'spencer owen'
license 'GPLv3'
summary 'Puppet GitLab Module'
description '# gitlab #


####Table of Contents

1. [Overview](#overview)
2. [Module Description - What the module does and why it is useful](#module-description)
3. [Setup - The basics of getting started with [Modulename]](#setup)
    * [What [Modulename] affects](#what-[modulename]-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with [Modulename]](#beginning-with-[Modulename])
4. [Usage - Configuration options and additional functionality](#usage)
5. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
5. [Limitations - OS compatibility, etc.](#limitations)
6. [Development - Guide for contributing to the module](#development)

##Overview

The spencerowen-puppet module installs a fully self contained gitlab server on an ubuntu server

Tested :
Gitlab 6-0-stable on Ubuntu 12.04  
Gitlab 6-1-stable on Ubuntu 12.04  

 

##Module Description

This puppet module accomplishes the gitlab 6 installtion tasks outlined in the install.md 
https://github.com/gitlabhq/gitlabhq/blob/6-1-stable/doc/install/installation.md?source=cc





##Setup

###What spuder-gitlab affects

The module installs the following programs:

installs ruby 2.0 (from saucy ppa\'s)  
nginx server  
postfix server  
mysql server  

The module configures the following files:  

/home/git/gitlab/config/gitlab.yml  
/home/git/gitlab/config/database.yml  
/home/git/gitlab/config/unicorn.rb  
/home/git/gitlab-shell/config.yml  
/etc/init.d/gitlab  
/etc/ngnix/sites-available/gitlab  
/etc/nginx/sites-enabled/gitlab  

###Setup Requirements **OPTIONAL**

This module requires the following programs

puppet >= 3.3.0  
ruby   >= 2.0 (installed automatically)  


spuder-gitlab automatically installs the following dependencies

puppetlabs-apt
puppetlabs-mysql >= 2.0.0
example42/postfix
jfryman-nginx
maestrodev/wget


The following dependencies should be resolved automatically

git  		>=1.7.10
ruby 		>=2.0.0
- bundler
- mysql2
-ruby2.0
-charlock_holmes
mysqlserver
mysqlclient
ngnix
postfix


You can safely ignore the following warnings that are presented durring installation
Certain versions of puppet return these errors even though the packages were installed properly

Warning: Failed to match dpkg-query line "No packages found matching mysql-client.\\n"  
Warning: Failed to match dpkg-query line "No packages found matching mysql-server.\\n"  
Warning: Failed to match dpkg-query line "No packages found matching libxslt1-dev.\\n"  
Warning: Failed to match dpkg-query line "No packages found matching python-docutils.\\n"  
Warning: Failed to match dpkg-query line "No packages found matching libicu-dev.\\n"  
Warning: Failed to match dpkg-query line "No packages found matching git-core.\\n"  
http://projects.puppetlabs.com/issues/22621  


The install process may take a long time, and may appear to be stuck at the following line for up to 600 seconds:   
Debug: Executing \'/usr/bin/yes yes | bundle exec rake gitlab:setup RAILS_ENV=production\'



	
###Beginning with spuder-gitlab	

To use the module, you must have mysql::server installed and configured with a user. 
It is recomeded that this be setup in your site.pp file, hiera or another ENC.


If you are using puppet stand alone, the following would setup mysql

root$ import module puppetlabs-mysql

root$ cat /tmp/gitlab-mysql-prerequisits.pp  
  class { \'mysql::server\':  
    config_hash => { \'root_password\' => \'badpassword\' }  
  }  
  
puppet apply /tmp/gitlab-mysql-prerequisits.pp

  

	 
##Usage


After the mysql root user has been steup, call the gitlab class with the desired parameters. 
Any parameters omitted will be set to the defautls located in gitlab::params

For example, a basic configuraiton might look like this: 

      class { \'gitlab\' : 
	  git_email              => \'git@foo.com\',
	  git_comment            => \'GitLab\',
	  gitlab_branch          => \'6-1-stable\',
	  gitlabshell_branch     => \'v1.7.1\',
	  
	  gitlab_dbname          => \'gitlabdb\',
	  gitlab_dbuser          => \'gitlabdbu\',
	  gitlab_dbpwd           => \'changeme\',
	  

	  gitlab_projects        => \'10\',
	  gitlab_username_change => true,
	  
	  }
	  
Compare tests/init.pp for a working example of setting up gitlab
	  
	  
##Reference

All of the parameters that can be set



  
    #Gitlab server settings
    $gitlab_branch         
    $gitlabshell_branch     
    $git_user               
    $git_home               
    $git_email              
    $git_comment            
    $gitlab_sources         
    $gitlabshell_sources    
    
    #Database
    $gitlab_dbtype          
    $gitlab_dbname          
    $gitlab_dbuser         
    $gitlab_dbpwd           
    $gitlab_dbhost         
    $gitlab_dbport          
    $gitlab_domain         
    $gitlab_repodir        
    
    #Web & Security
    $gitlab_ssl             
    $gitlab_ssl_cert        
    $gitlab_ssl_key         
    $gitlab_ssl_self_signed 
    
    #LDAP
    $ldap_enabled           
    $ldap_host              
    $ldap_base           
    $ldap_uid              
    $ldap_port          
    $ldap_method         
    $ldap_bind_dn           
    $ldap_bind_password     
    
    #Company Branding
    $use_custom_login_logo 
    $company_logo_url       
    $use_custom_thumbnail  
    
    #User default settings
    $gitlab_gravatar        
    $user_create_group      
    $user_create_team       
    $user_changename        
    
    #Project default features
    $project_issues         
    $project_merge_request  
    $project_wiki           
    $project_wall           
    $project_snippets       
    $gitlab_projects 
    $project_public_default     

	  
	  
##Limitations

Designed and tested for Ubuntu 12.04
Should work on Ubuntu 14.04
May work on Debian 7
Will not work on CentOS / RHEL


##Development

Pull Requests are accepted: 


##Release Notes/Contributors/Etc **Optional**

This module is based on the work done by the following people:

sbadia - https://github.com/sbadia/puppet-gitlab  
atomaka - https://github.com/atomaka/puppet-gitlab  

##Changelog
2013-Oct-3: 0.1.0 First Release, fully tested
2013-Oct-5: 0.2.0 Removes ruby repo from files, and instead downloads from web  
Fixes https://forge.puppetlabs.com/spuder/gitlab    
2013-Oct-5: 0.2.1 Adds module dependencies
2013-Oct-7: 0.2.2 Fixes puppetlabs-mysql api change https://github.com/spuder/puppet-gitlab/issues/1   
2013-Oct-9: 0.2.3 Changes puppetlabs-apt dependency from 1.3.0 to 1.0.0
2013-Oct-9: 0.2.4 Fixes backup issue when replacing thumbnail icons https://github.com/spuder/puppet-gitlab/issues/8'
project_page 'https://github.com/spuder/puppet-gitlab/blob/master/README.md'

## Add dependencies, if any:
# dependency 'username/name', '>= 1.2.0'
dependency 'puppetlabs-apt', '>=1.0.0'
dependency 'puppetlabs/mysql', '>=2.0.0'
dependency 'jfryman/nginx',	'>=0.0.5'
dependency 'maestrodev/wget',	'>=1.2.2'
