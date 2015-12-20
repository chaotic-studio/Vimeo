###  This is a fork of the official Java SDK for Vimeo API 3.0

My goal for this fork is to improve the parts that I believe are not implemented the way they should be. Normally I would have simply submit a pull request to the original, but in this case I think that my desired changes would be to different from the original design to be appropriate.
***
To use this api you’ll first need to register your app from Vimeo:

https://developer.vimeo.com/apps

Then you'll need to generate an Access Token with upload access.
The generated Token is all you need to use the Java Vimeo API 3.0.
***
```java

package org.chaotic-studio.vimeo;

import java.io.File;

public class VimeoSample {

  public static void main(String[] args) throws Exception {
    Vimeo vimeo = new Vimeo("[token]"); 
    
    //add a video
    boolean upgradeTo1080 = true;
    String videoEndPoint = vimeo.addVideo(new File("/Users/tmendici/Downloads/Video.AVI"), upgradeTo1080);
    
    //get video info
    VimeoResponse info = vimeo.getVideoInfo(videoEndPoint);
    System.out.println(info);
    
    //edit video
    String name = "Name";
    String desc = "Description";
    String license = ""; //see Vimeo API Documentation
    String privacyView = "disable"; //see Vimeo API Documentation
    String privacyEmbed = "whitelist"; //see Vimeo API Documentation
    boolean reviewLink = false;
    vimeo.updateVideoMetadata(videoEndPoint, name, desc, license, privacyView, privacyEmbed, reviewLink);
    
    //add video privacy domain
    vimeo.addVideoPrivacyDomain(videoEndPoint, "clickntap.com");
   
    //delete video
    vimeo.removeVideo(videoEndPoint);
    
  }

}
***
The class VideoResponse provides response code and json response, see Vimeo API documentation to check errors.

### Use with Maven

```xml

<dependency>
  <groupId>org.chaotic-studio</groupId>
  <artifactId>Vimeo4J</artifactId>
  <version>1.0</version>
</dependency>

```
### Support or Contact
Having trouble with Vimeo4J? Contact support@chaotic-studio.org and I will help you sort it out.
