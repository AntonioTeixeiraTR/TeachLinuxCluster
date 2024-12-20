# TeachLinuxCluster
Repository to teach pacemaker to TR audience

Link for the Workshop/Demo: 

https://trten-my.sharepoint.com/:v:/r/personal/antonio_teixeira_thomsonreuters_com/Documents/Recordings/LINUX%20CLUSTER%20OVERVIEW-20241219_120229-Meeting%20Recording.mp4?csf=1&web=1&e=s3rs9a&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D

if you happen to not have access, ask Stephanie Lorefice for it she will be able to provide you with a copy

# Software required to Run this LAB

  VirtualBox-7.1-7.1.4_165100_fedora40-1.x86_64

  vagrant-2.4.3-1.x86_64

   # vagrant plugin list
     vagrant-persistent-storage (0.0.50, global)
 

  ** I am using Fedora 42 alpha version, but this works in all modern linux distributions that you might want use.
  Ps.: I did not test it in Windows Service for Linux implementations or NESTED virtualization with KVM, but you are more than welcome to be a pionner and document this effort.

  # The environment

  These softwares along with the directory/files provided here are meant for educational purposes only, everything provided here are opensource and predicted to be used inly to learn pacemaker cluster in a "real" environment.
  Nothing done in these codes were tought to be best practices or even used in a "from/to" effort to create productions environment. in fact they are Bad practices for any attempt to reproduce it on even Dev environment. 
  They way it was done is purely to foster the Didatics and explanations.

  With that said, the environment produced is a Broken Pacemaker cluster that you have to fix ----> Watch the video in the link and you will get necessary details.

  # To start the environemt in the directory that have the vagrantfile of your linux, all you have to do is :

  vagrant up ( or vagrant up --provider=vbox if you have more than one hypervisor in your system )

The Vagrantfile predict a very big usage of memory and cpu of your phisical machine, if you have the resources, fine go with it, if not you will have to adjust it to what you have and wait a little longer to the provision to complete.


I hope you guys enjoy learning from it as much as I enjoyed Building it

:)

Fave fun!

Antonio.

  

