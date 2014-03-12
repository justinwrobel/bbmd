# Autostart Developer VM

    cd /etc/init.d
    wget https://raw.github.com/justinwrobel/bbmd/master/blackboard -O /etc/init.d/blackboard
    chmod +x /etc/init.d/blackboard
    chkconfig \--add blackboard #adds blackboard to the startup procedure
finally, either restart or type `service blackboard start` and blackboard should start up.

# Setup remote debugging

Add the following to /usr/local/blackboard/apps/tomcat/conf/wrapper.conf.bb:

    wrapper.java.additional.28=-Xdebug -Xrunjdwp:transport=dt_socket,address=8000,server=y,suspend=n

# Setup VM networking
This one only applies if you have installed BB rather than used the VM 
 * Attached to: NAT
 * Port Forwarding
   * 80 -> 80 #Super important, Blackboard does not play nice on other ports.
   * 22 -> 22 #ssh 
   * 1521 -> 1521 #sql
   * 8000 -> 8000 #Debugging

##Sources & Inspiration
 * http://www.edugarage.com/display/BBDN/Installing+Oracle+and+Blackboard+on+Centos
 * https://help.blackboard.com/en-us/Learn/9.1_SP_12_and_SP_13/Administrator/230_Developer_Resources/Developer_Virtual_Machine
