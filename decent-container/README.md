Hi There, 
I see you are interested in this pretty decent looking container.

Well hold your horses there buddy, we have a few things that need to be addressed!

You might be tempted to think all the source code in voat is where the action is.

Well, you'd be sorely mistaken, and rightfully so, you were working on it in that folder all along!

Let me tell you how I have horribly mangled things!

Anything python/uswgi is sitting in application (this is the application/python container)

Anything nginx related is in nginx! This is acting as a proxy for gunicorn, gunicorn does all the leg work...

Obviously postgres is where the db is!

Now, this is a start but no means a finish, I am having weird issues with starting the service...

So far it would seem that we are operating based on hard-coded or at least somewhat assumed directories, I have tried to clean
what I can find, but it's far from perfect, so please have a look, hack on it for a bit and try and integrate your updates into the container; for my sanity as well as yours!

For your peace of mind, 

presume that the working root directory starts at /decent-container/ 
(aka if there is a folder in decent-container/application/var/ the container will see it as /application/var)

It is vitally important that you do NOT rename the root directory folder, as networking and interconnected-ness and like the zen of the whole thing, rests entirely on the root folder name... 

