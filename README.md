# Ufo3
*   **Formulate a hypothesis/problem statement about behavior of ping times of these three servers.**

Based on the provided information stating that the 3 servers are located around the world, I would expect my test results to wary. The further away the server is, I should expect a higher/longer response time. 


*   **Plan an experiment, which measures response times of these three servers.**

I want to test my hypothesis by using "Git Bash" or "CMD" (Windows) / Terminal (Mac) and pinging each server times by using the "ping" command, in which the server is send a 32 byte data packet and the sender awaits for a response. While the "ping"-command already performance 4 pings to the server and provides both "minimum", "maximum" and "average" results, I want to get a broad set of results to minimize potential errors.  
I'll be conducting the experiment from my apartment on Nørrebro, Copenhagen. I made sure that only my cmd-window was open, along with the chrome-browser displaying my google doc in which I could record the results. 
 
I will perform the same experiment by creating and using a temporarily Digital Ocean droplet placed in San Francisco running Ubuntu 18.04 and record the results. 




*   **Execute the experiment, which measures response times of these three servers.**

Test results can be found here: 
[https://docs.google.com/spreadsheets/d/1ac-mX86fk20l-HJUBVq_NCuog_QiaE6XUaNrICiyJqw/edit#gid=0](https://docs.google.com/spreadsheets/d/1ac-mX86fk20l-HJUBVq_NCuog_QiaE6XUaNrICiyJqw/edit#gid=0)

See also attached pictures in the "Server Ping Results"-folder for the raw experiment data/result documentation. 




*   **Evaluate your experiment and interpret the measurements and results.**

**Copenhagen Results** 

From the collected data, we are able to determine that:



*   The server with the longest response time was 128.199.144.199, with an average of about 210 milliseconds. 
     *   The servers slowest recorded response time was 214 ms
            *   This result was also from the Ping 1.1, meaning the very first ping to the server
        *   The fastest result was 210ms.
    *   Server 167.99.51.33 was in the second-fastest (or slowest, depending on if you are a "glass half-empty/half-full" person) with an average response time of 87 milliseconds. 
        *   Its slowest response was an astonishing 126 ms, but excluding that one-time-fluke during ping 3.2 and the very first ping at Ping1.1 which was at 91ms., it was in general more about 88ms.
        *   Its fastest recorded response was 87ms 
    *   Server 46.101.253.149 had the fastest response time with an average of about 15 milliseconds.
        *   Its slowest response came from the være first Ping1.1 at 20ms and a single 19ms at Ping 3.1. 
        *   The fastest response came in at 15ms.
    *   All packets, 20 send and 20 received , was send and received and no one was lost during the experiment. \


Diving further into the results:



*   The slowest server (128.199.144.199) average response time (210ms) was about 14x times slower than the fastest average (15ms) from 46.101.253.149
    *    This might not seem as much since we are dealing with results in milliseconds, but imagine we needed to send and receive of queries in the thousands or even millions like Facebook, and a few milliseconds suddenly becomes all important.
    *   This type of response time would not even be suited for online video games were response-time is crucial, such as shooters, real time strategy games or racing games. For Turn-based games however, such as chess, checkers or Civilization, it would be fine.  
*   The fastest average response time of 15ms (46.101.253.149), was about 5.8x times faster, than the seconds fastest average time of 87ms by 167.99.51.33.
*   All experiments showed that the response from first Ping (Ping1.1) to each server was slightly higher than the following pings, perhaps because the machine performing the ping had to zero in on the location.
*   Ping 3.2 in 167.99.51.33 produced a one-off response of 126ms, which was about 40ms higher than the general average response time from the same server. This was the highest spike when testing any of the servers, by about 45%!. 

By using [https://www.iplocation.net/](https://www.iplocation.net/) I learned where the servers are approximately located in the world :



*   128.199.144.199 - Singapore
*   167.99.51.33 - New Jersey, America
*   46.101.253.149 - Frankfurt, Germany

 \
This led me to further investigate how much distance my ping had to cover in order to get a response, using [https://www.distancefromto.net/](https://www.distancefromto.net/) to get an approximate distance.

Approximate (Air)Distance from Copenhagen to the servers:



*   Singapore: 9972km 
*   Frankfurt, Germany: 671km
*   New Jersey, America: 6271km

 
The approximate (air)distance between the servers and the San Francisco server is:



*   Singapore: 13597km 
*   Frankfurt, Germany: 9143km
*   New Jersey, America: 4115km

Comparing the results with the approximate locations of the servers and the (air) distance between my test machine in Copenhagen and the servers, it made sense that:



*   The server placed in Singapore would provide the slowest average response
*   The server in New Jersey, America gave the second  fastest average response
*   The fastest average response was being delivered by the server in Frankfurt Germany.
*   It's interesting to note that:
    *   As previously pointed out, the fastest average response time was 14x faster (Frankfurt-server), than the slowest average response time (Singapore-server). Looking at the approximate distance that the ping had to travel, it actually also almost matches, since the ping had to travel about 14.8x times longer to reach the server in Singapore (9972km), than it had to with the server in Frankfurt (671km)
    *   When comparing the distance between the responses from Frankfurt and New Jersey, Frankfurt's average response time was 5.8x times faster than New Jersey, but the (air) distance was almost 10x times longer to New Jersey, than to Frankfurt. This underscores that "x times faster is not equal to the same x times longer distance ". Perhaps the reason for the better "faster response time over long distance" was to New Jersey than Singapore might be better infrastructure.

**The San Francisco results**

I used the following command to ping 4 times and set the packet to 32 bytes 



*   ping -s 24 -c 4 [ip]
    *   the -s 24 sets the size of the packet, but Ubuntu (?) adds 8 additional bytes when sending, so setting it to 32 would result in 40 being sent 
*   The slowest average response was to Singapore, at 179ms, with the lowest response coming in at 179ms and the highest at 180ms.
*   The second fastest was when pining Frankfurt, with an average of 155ms, 155ms being the lowest and 156ms being the highest.
*   And (no surprise), the fastest with an average of 72.1ms we have New Jersey, with the lowest being 72.0ms and the highest response being 72.9ms.

So what's so interesting about the SF results?



*   Despite the San Francisco and Singapore being about 13597km apart, the average response time is still faster at 180ms, than from Copenhagen to Singapore, which average response time was recorded at 210ms at a distance about 9972km. That's a difference of around 30ms and about 3600km! 
    *   Great internetlines in the pacific ocean connection the American continent with Asia? \
 
 

*   The distance between SF and  Frankfurt is about 9143km, with an average response of 155ms, the distance between Copenhagen and Singapore is about 9972km ( so only about 800km longer) with an average response of 210ms. It's a difference of 50-55ms over just about 800km, which seems like a lot of extra ms over a short distance.

    At the same time, take look at the data between the SF- Singapore. They are about 13597km (over 3600km longer) apart, but has an average response time of just 179ms, compared to the 9143km between SF - Frankfurt with its average response time of 155ms.         

    *   Once again pointing to some weak or inferior connection between Frankfurt and San Francisco, compared to San Francisco and Singapore.
        *   Perhaps this is a general trend for EU? It looks like one gets a better result pinging from the US to Asia, than pinging from EU to Asia.
        *   Is this because America "invented the internet" and build a strong infrastructure? 
            *   That would be kinda ironic, since US Domestic internet is considered very bad compared to EU, due to monopoly internet providers and the Trump administration lowering the requirements for what is supposed to be considered "standard internet" in the country (originally set by the Obama administration)
*   Copenhagen to New Jersey is about 6271km with an average response of 87ms. At 4115km, the distance between San Francisco and New Jersey is about 2100km shorter, so we should expect a lower average response time (and we do) for SF to NJ, but the average response was "only" measured to be about 72.1ms.
    *   So despite a 2100km distance difference, the average response difference is only about 15-17ms, which is about the same average response time between Copenhagen and Frankfurt, but that distance is only about 671km! \
It means that SF to NJ covers 2100km at the same average ms rate/speed, as the distance between Copenhagen and Frankfurt does at 671km.
*   SF to Singapore: About 13597km at a average response time of 179. \
Copenhagen to Frankfurt: about 671km at about 15ms in average response.
    *   Despite the distance between SF and Singapore being close to 20x times longer than from Copenhagen to Frankfurt, the average response time in ms is only close to 12x from Cph to Frankfurt, once again pointing towards some slow internet connections between regions.

**Discuss what you are measuring, how you are measuring, and what could influence your results.
See Peter Sestoft "Microbenchmarks in Java and C#"[https://www.itu.dk/people/sestoft/papers/benchmarking.pdf](https://www.itu.dk/people/sestoft/papers/benchmarking.pdf) for inspiration 


**Experiments can be re-created… But never truly be perfect or controlled.** \
Through my experiments, I have measured how long it takes for a server to respond to a request and produce the result in milliseconds. I've done this by running the experiment on both my own desktop-machine, which is equipped with the following hardware, located in my apartment on Nørrebro, Copenhagen : 


*   Windows 10 Pro 64-bit with the October 2018 update
*   Intel i7-6700K CPU 4-Core/8-Thread
*   16 GB DDR4 Ram
*   Nvidia 980 TI 6GB DDR5 GPU
*   2x 512GB SSD + 1x 2TB HD 
*   Wired Internet100/100 Mbit/s (According to [http://xn--bredbnd-ixa.dk/hastighedstest](http://xn--bredbnd-ixa.dk/hastighedstest)) 

I also executed the same experiment through a basic Digitalocean Droplet in San Francisco, with the following specifications: \


*   Ubuntu 18.04 x64
*    1 vCPU
*   25GB SSD
*   1GB Memory
*   1TB Transfer

The linked article talks about "_... biological experiments, such as measuring bacterial growth, are influenced by natural variation and many unknown circumstances_" compared to software experiments, because we (the user) can control all the aspects of the experiment since we can build/select the hardware and run the experiment with all the conditions and variables set to what we want. \
 
At least, that's the theory. 


In practice however, it's rare that we truly controle all the conditions of an experiment. Take my first experiment as an example in my apartment in Nørrebro. Sure the hardware and software can be replicated, but what about the internet connection? When I ran the internet speed test, who is to say that the result couldn't change the next time I run test, simply because I live in a apartment complex with 10+ apartments that all share the same connection and maybe 50% of the user decided to use the internet? Time of day plays a huge part of the experiment and one that I did not think about until I started writing this report. This also applies to the experiment conducted from the San Francisco server, because while I might be conducting the experiments at 11:00pm danish time, SF is 9 hours behind, so that would mean the server is conducting the test at 2:00am local time in SF.

During one test, I experienced a sudden spike in response time, might this have been caused by a sudden heavy load on the apartments internet connection? Who knows. 

The article also talks about testing and benchmarking with Java, using the fact that by using the Java Virtual Machine to execute and run the experiments, one has effectively created a small "black box"-solution that can be run on multiple platforms. The results from the experiments can therefore only be affected by the hardware it is being run on, while the code inside the box will remain the same, no matter what platform it is run on. 

For my experiments, I ran my experiment on my desktop using the Windows 10  command-prompt and the "ping"-command, while I had to use Git Bash in order to connect to the Ubuntu server in San Francisco server and manually set my ping-command, in order to proper reproduce the experiment. However, the results might have been different if I had run my first experiment on my MacBook, which is running OSX (Unix).  
 
So given all these factors, what could interfere with my experiments?

*   The apartments Internet Connection speed
*   Hardware configuration
*   OS
*   Other software running in the background (Discord, Steam, Battle.net, Firewalls)
*   Versions of software, such as Windows
*   Throttling of the server I was testing against
*   Time zones and traffic-load

**A too simple experiment?**

The article describes a experiment in which the author writes a small Java application to 

" _measure CPU time, memory access time and any associated systems overhead. This may be used to compare different data structures or algorithms, to compare different implementations of methods, or to compare speed of access to different levels of the memory hierarchy._"

For my experiment however, I just wanted to know how fast a server could response to a request and thus I chose not to build a app or write any code for that matter, but to use the build-in tools that where available in pretty much all command-tools in a operating system.

The upside of choosing to use the "Ping"-command was that it made it possible for me to quickly get started running my experiments, but on the other hand I was using tools designed, build and pretty much locked down by the developers, thus I would have had a difficult time changing (some) settings to my preference, compared to if I had build a Java app from scratch and had access to the source code.

My thinking using the Ping-tools rather than building something was also based on the thought, that even if did build something from scratch the outcome would be the same. The "app" would simply return the response time, just like the available tools already provided. The assignment was not to perform a specific function or calculation, other than testing how fast the server could respond. Had the experiment required me not only to measure the response speed, but also the servers capabilities and hardware, such as CPU etc., then a building an app would have been the only solution. 

Another benefit of doing the app in Java for example, would mean that any test environment that could run java, could run the app and the experiment (pretty much) out of the box.

**Final thoughts**

Despite the simplicity of the assignment, it was quite interesting studying the results and speculate why certain results ended up the way they did. I play a lot of online games and know that a ping crossing above 100+ often means the player can experience gameplay problems and result in them perform badly. Seeing pings above 100+ just pining America during the test was not a surprise to me, but in retrospective it is truly incredible that some online games let you play against players from America and Asia, and yet my own ping is between 20-50ms, meaning there must have been some incredible network engineers and coders working on getting online experience running as smoothly as possible. 
