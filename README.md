# EnerNOC OpenADR 2.0 VTN

This is the section developement version of EnerNOC's open source VTN (server) for 
[OpenADR 2.0](http://openadr.org).  

This app supercedes the original VTN, the major difference being the underlying web framework 
was migrated from [Play 2](http://www.playframework.com/) to [Grails](http://grails.org/).
Grails is a much more mature web framework while Play 2 had some missing features.
The original Play app required work-arounds for common features such as services and 
dependency injection, which Grails provides out of the box.

## Configuration

Most application settings are found in `gails-app/conf/Config.groovy`.  Set the `xmppSvc`
settings in order to enable XMPP functionality.  Note that if using OpenFire as the 
XMPP server, `jid` should be just the 'username,' not `username@host.com`


## Development

### Prerequisites

The VTN depends on the oadr2-ven code found here: http://github.com/enernoc/oadr2-ven

Install locally by running 

    ~/oadr2-ven $ mvn install -Dmaven.test.skip=true

### Running Locally

The app can be run from the command line with Apache Maven or the Grails command line tools.

If you have Grails installed: `grails run-app`

If you use Maven:

    export MAVEN_OPTS="-Xmx512m -XX:MaxPermSize=256"
    maven grails:run-app

For more info, see: http://grails.org/doc/latest/guide/commandLine.html#4.5%20Ant%20and%20Maven 


### Testing Locally

You can use `curl` to execute OpenADR requests on the server like so:

    curl -vd @xmpp-http-tests/httpRequest1.xml -H "Content-Type: application/xml" \
       http://localhost:8080/oadr2-vtn-groovy/OpenADR2/Simple/EiEvent
    


### Packaging

Using grails command line: `grails war`

or with Maven: `mvn package`


## TODO

* OpenADR Debug page to post example XML from a web form and display the result
* Filter on OpenADR services to handle certificate auth
* Web app auth
