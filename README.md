It is **Adobe Air** library written in **AS3** for caching content
(swf,images,data file) to the local file system.
    
The library is fully compatible with **Loader / URLLoader/ NetStream** and it try to replace a very light weight version of the browser cache.
     
By using this class , the data of images text  and video will be fetch from server once and save locally , and then every time you will be request again we will check the local file system first and if the local file exists it will be use. 
     
     
As a result , you can eliminate unnecessary communication to the server by requesting the same file over and over again.
    
The usage is exactly the same as Loader / URLLoader /NetStream.
The main difference is that the initialization process that requires 3 Lines of code.

        1. the fist is specified the application the main cache directory.<br>
        2. is passing the  LocalCacheLoader, LocalCacheURLLoader, LocalCacheNetStream.
        3. Using the factory to create instances for those classes. <br>
     
p.s 
It is not obligatory to use a Factory class to generate the local loader classes.    
    
Help is needed!
---------------
        Help is needed for the NetStream loader it doesn't have the optimal solution it first save the
        file to local disc and then play.
        it will be perfect if it could buffer the stream and in end create file out of it.
     
    
     
## Code Example
Let's look at an example even that it is quite easy to understand. File is in  **sample/main.as**
    
     
    
     
        // Setup cache Directory.
        // Can be cached in the directory that you specify here .
        LocalCacheSettings.WORKING_DIRECTORY = File.applicationDirectory;
        
        // Please set the following: If AIR for Android, the AIR for iOS.
        // LocalCacheSettings.WORKING_DIRECTORY = File.applicationStorageDirectory;
     
        // Init Factory Class.
        // Loader like normal will be used if you do not initialize the factory class .
        NetClassFactory.initialize (LocalCacheLoader, LocalCacheURLLoader, LocalCacheNetStream);
     
        // Create Class.
        // If true the second argument here , regardless of there without a cache that is stored in the local
        // I will take the file from the Web always on .
        _loader = NetClassFactory.createLoader (null, false);
        / / I use normally after .
        _loader.contentLoaderInfo.addEventListener (Event.COMPLETE, _onComplete);
        _loader.load (new URLRequest ("https://www.google.co.jp/images/srpr/logo11w.png"));
     
     
    Fork from https://github.com/sgmnt/LocalCacheLoader
    It has been fork mailly for translation resone (from japanis)

 