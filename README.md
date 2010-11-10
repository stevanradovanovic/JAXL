# JAXL (Jabber XMPP Client and Component Library in PHP)

Jaxl 2.x is an object oriented XMPP framework in PHP for developing real time applications
for browsers, desktops and hand held devices. Jaxl 2.x is a robust, flexible and easy to use
version of Jaxl 1.x series which was hosted at google code.

* More robust, flexible, scalable and easy to use
* Event mechanism for registering callbacks for various xmpp events
* Integrated support for Real Time Web (XMPP over Bosh) application development
* Support for DIGEST-MD5, PLAIN, ANONYMOUS, X-FACEBOOK-PLATFORM authentication mechanisms
* 23 implemented XMPP extensions [(XEP's)](http://xmpp.org/extensions/) including MUC, PubSub and PEP
* Setup dynamic number of parallel XMPP sessions on the fly
* Options for monitoring, usage stat collection, rate limiting, etc.

## Download

* For better experience download [latest stable tarball](http://code.google.com/p/jaxl/downloads/list) from *google code*
* The development version of Jaxl is hosted here at *Github*, have fun cloning the source code with Git
* Checkout Jaxl 1.x series source code from [svn repository (deprecated)](http://code.google.com/p/jaxl/source/browse/)

Warning: The development source code at Github is only intended for people that want to develop Jaxl or absolutely need the latest features still not available on the stable releases.

## Using JAXL library

Jaxl library is based on events. Register callback(s) inside your application code for required XMPP events and write your app logic inside callbacks. Here is how one can send an XMPP chat message using Jaxl library:

    // Include and initialize Jaxl core
    require_once '/path/to/jaxl/core/jaxl.class.php';
    $jaxl = new JAXL(array(
        'user'=>'username',
        'pass'=>'password',
        'host'=>'talk.google.com',
        'domain'=>'gmail.com',
        'authType'=>'PLAIN',
        'logLevel'=>5
    ));

    // Send message after successful authentication
    function postAuth() {
        global $jaxl;
        $jaxl->sendMessage('anotherUser@gmail.com', 'Test message using Jaxl library');
        $jaxl->shutdown();
    }

    // Register callback on required hook
    JAXLPlugin::add('jaxl_post_auth', 'postAuth');

    // Start Jaxl core
    $jaxl->startCore('stream');

## Useful Links

* [PHP Documentation](http://jaxl.net/)
* [Developer Mailing List](http://groups.google.com/group/jaxl/)
* [Issue Tracker](http://code.google.com/p/jaxl/issues/list?can=1&q=&colspec=ID+Type+Status+Priority+Milestone+Owner+Summary&cells=tiles)

Generate Jaxl documentation on your system for quick reference:
    
    phpdoc -o HTML:Smarty:PHP -ti "JAXL Documentation" -t /var/www/ -d xmpp/,xep/,env/,core/

