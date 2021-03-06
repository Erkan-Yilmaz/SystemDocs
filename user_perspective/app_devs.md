# Builders

The seemingly eternal question of the business model particularly for Open Source developers. Is it build applications to support them? or perhaps provide consulting? None of these seem to have much to do with the core skill of the developer, that is coding.  What about commercial applications, how much to charge, what revenue model, how many users etc. these are all questions start-ups and existing projects must evaluate. What if the answer to both of these questions was, provide something people value and you will be automatically rewarded!

##Let the network measure the value

In the MaidSafe network computers who provide resource are awarded an opportunity to request a safecoin. This mechanism can be considered in this following simplified form. (N.B. messageid is a random number on the network, it is not settable to a known mine attempt by client apps)

    if (messageid % current_rank == 0)
      Mine_Attempt (sign coin with vault key over to client that owns that vault)

This is triggered on data Get requests, so popular data, but mining frequency is based on stored data (current_rank). Client applications access the network through the Nfs layer. This is where the PUT GET DELETE mechanism happens. Here application developers will add a field to GET and that is a wallet address (or ID) of the client application provider. So developers build an app and insert their wallet address in the client software they build. This address will be inserted in every GET request the client makes on the network. So from the above example we multiply by a factor of 10 (devs always get 10% of safecoin). so it becomes


    if (messageid % (current_rank  * 10) == 0)
      (Mine_Attempt (sign coin with vault key for client address contained in Get request, i.e. the developer).
    else if (messageid % current_rank == 0)
      Mine_Attempt (sign coin with vault key over to client that owns that vault)

##Can this be gamed ?

There are several issues that will pop into many minds and it is a good idea to discuss each of these individually.

* What if somebody copies an application and changes the wallet address?
* What happens if a developer creates an application purely to issue Get requests?

The answers are not all that difficult to find. Some analysis could show that:

Copying of code is an attribute anyone can do. In some cases copy is protected in law and in other cases the protection is handled by market forces. A good application will be the one people adopt, not the one they copy and alter. Applications that attain first mover advantage or simply network effect will outlast any cheap copies that are less well thought out. Applications that do not perform well or fall behind, may in fact be forked and improved. This is a good thing for consumers to. Later we will see this is not a model where people download applications anyway, they are already installed, making copies potentially impossible.

This is a situation the network handles itself. Multiple Get request would mean data comes from cache, thereby no earning capability will come from this.  If apps randomly choose addresses to retrieve, the application will be sluggish for a start, also the network will not allow range based searches. Such activity can easily trigger a ‘no-mine‘ signal to the managers of the wallet in question. Thereby preventing any coin being created and a sluggish user experience. These applications would likely not be widely sought after.

##Additional advantages for application developers

As MaidSafe shares data at the file system level, applications can be shared just as easily as a web page.  This means that an application is pre-installed as users wish to use them. No installers are required any more. In addition as the applications would exist on a public share, then no virus attacks on the binary is possible. This reduces developers route to market and ensures a clean and tested user experience. Many applications disappoint with poor installers or installation mechanisms. In a decentralised Internet, these issues just are not there.
