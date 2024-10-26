Android Dropbear
=========


Customizations
----

Much of the project is pre-configured with sane defaults, but if you'd like to customize the behavior of Dropbear for Android, here are a few tips.
1) To change/configure most options, look in and modify the following files as appropriate:  
	a) default_options.h  
	b) sysoptions.h  
	c) config.h  

For instance, to change the port Dropbear runs on or to change the default location in which Dropbear tries to generate keys, edit ``default_options.h`` and modify the respective values.  
  
Basic usage
----
Dropbear for Android adds a few special flags to Dropbear:  
- A: signifies Android mode and allows for password authentication in the absence of the ```crypt()``` lib
- G: allows us to specify the GID dropbear should run as  
- U: allows us to specify the UID dropbear should run as  
- N: specify the login username for the session  
- T: specify the authentication key for the session  

A typical usecase would be:  
```
./dropbear -d /path/to/dropbear_dss_host_key -r /path/to/dropbear_rsa_hostkey -p 10022 -P /path/to/dropbear.pid -R -A -N user -C password -U u0_aXX -G u0_aXX
```

The above command will run the Dropbear server with password authentication enabled for the user 'user' with password 'password' and will attempt to run as u0_aXX and in that group. More information can be found by issuing:  
  
```
./dropbear --help
````

Credits
----
Big thanks to mkj who has been maintaining Dropbear:  
https://github.com/mkj/dropbear  

Thanks to NHellfire who's work made the process of getting 2018.76 up and running much easier:  
https://github.com/NHellFire/dropbear-android  

Thanks to jmfoy for the ```config.sub``` and ```config.guess``` files:  
https://github.com/jfmoy/android-dropbear

Another thank you to the various other repositories out there whose various approches helped lead to this completed project.

已经将代码修改为android版本,可以在N5的Nethunter环境下编译出ARM32版本的, 在eadb 环境下编译出ARM64环境;

执行下面的config命令:
```
./configure --enable-static
```

具体可参考 release下面的配置好的tgz;