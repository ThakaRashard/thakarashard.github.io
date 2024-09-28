
# Currently Compiling

### [DragonBall GT](https://www.imdb.com/title/tt0139774/)
<iframe src="https://archive.org/embed/ikaos-som-dragon-ball-gt-complete-001-064-r2j-dragon-box-multi-audio-v2" width="640" height="480" frameborder="0" webkitallowfullscreen="true" mozallowfullscreen="true" allowfullscreen></iframe>

[JAY Z, Kanye West - Otis ft. Otis Redding](https://www.youtube.com/watch?v=BoEKWtgJQAU)
## The New social Disease
[LAndSat 7, retired?](https://www.usgs.gov/news/national-news-release/end-era-historic-landsat-7-mission-takes-final-images)
![SantaMonica](https://pbs.twimg.com/media/GYbTbDFaoAA1W5x?format=png&name=900x900)

# Broken Builds
Usually its in the .css/.scss file where my [build breaks](https://github.com/ricoThaka/compiling/actions/runs/11040779623/job/30784563669). i was porting some old code from BubblegumPop, a repo my friend an spouse uses to do something with her girlfriends when social media breaks... Now im being asked for new functionality bc `actions/upload-artifact@v4 or later` is not present. I had to add to the Buildfile and now the site and 3 other sites are not complaining and accepting new MarkDown and MarkUp [i shared a cheetsheet below ](#MArkDown-QuickFacts).

`Artifacts allow you to share data between jobs in a workflow and store data once that workflow has completed.`

### [About workflow artifacts](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/storing-and-sharing-data-from-a-workflow)

```log
Found 0 artifact(s)
##[debug]List artifact count: 0
Error: Fetching artifact metadata failed. Is githubstatus.com reporting issues with API requests, Pages, or Actions? Please re-run the deployment at a later time.
Error: Error: No artifacts named "github-pages" were found for this workflow run. Ensure artifacts are uploaded with actions/upload-artifact@v4 or later.
    at getArtifactMetadata (/home/runner/work/_actions/actions/deploy-pages/v4/src/internal/api-client.js:85:1)
    at processTicksAndRejections (node:internal/process/task_queues:95:5)
    at Deployment.create (/home/runner/work/_actions/actions/deploy-pages/v4/src/internal/deployment.js:66:1)
    at main (/home/runner/work/_actions/actions/deploy-pages/v4/src/index.js:30:1)
Error: Error: No artifacts named "github-pages" were found for this workflow run. Ensure artifacts are uploaded with actions/upload-artifact@v4 or later.
##[debug]Node Action run completed with exit code 1
##[debug]Finishing: Deploy to GitHub Pages
```



Like a pussy i turned off [linting](https://docs.github.com/en/contributing/collaborating-on-github-docs/using-the-content-linter). `The linter uses markdownlint as the framework to perform checks, report flaws, and automatically fix content, when possible. `  It was really helping me grow as an [HTML PRogrammer](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics) some argue its not a [Programming Language](https://github.com/resources/articles/software-development/what-is-a-programming-language) theres just different types and HTNL is a [Markup Language](https://en.wikipedia.org/wiki/Markup_language). From my understanding at this point [MarkDown](https://www.markdownguide.org/) is just a collapesed subset that reducses the steps to publish text to device. Like theres no [KramDown](https://kramdown.gettalong.org/) object or [Video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) without knowing [LiquiD](https://jekyllrb.com/docs/liquid/)



- [Rashard MRO](https://ricothaka.github.io/rashardmro/)

[Embedding videos #91 [KramDown User 2014]](https://github.com/mmistakes/minimal-mistakes/issues/91)

`I haven't been able to insert a video so far. I'm using:`
```html

<iframe src="https://www.youtube.com/watch?v=MU9sobaVx6I" width="560" height="315" frameborder="0"> </iframe>
```

[Is HTML a programming language? - theserverside.com](https://www.theserverside.com/feature/Is-HTML-a-programming-language)


# The Build File 

Here is the old Build file and the added and updated file is belo, i embedded a gist to see if my browser will throw that 200error

```yml
on:
  push:
  pull_request:
    types: [opened, synchronize]
jobs:
  build:
    runs-on: ubuntu-latest
    name: script/cibuild
    steps:
      - uses: actions/checkout@v2
      - uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3.2.0
          bundler-cache: true
      - name: build
        run: script/bootstrap
      - name: test
        run: script/cibuild
```

### updated

```yml
on:
  push:
  pull_request:
    types: [opened, synchronize]
jobs:
  build:
    runs-on: ubuntu-latest
    name: script/cibuild
    steps:
      - uses: actions/checkout@v4
        uses: actions/jekyll-build-pages@v1
        with:
          source: ./
          destination: ./_site
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
      - uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3.0
          bundler-cache: true
      - name: build
        run: script/bootstrap
      - name: test
        run: script/cibuild
  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```




<script src="https://gist.github.com/ricoThaka/566d7f15a49f45fc5f782f3448caa778.js"></script>


## MArkDown-QuickFacts

# [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
Create sophisticated formatting for your prose and code on GitHub with simple syntax.

# A first-level heading
## A second-level heading
### A third-level heading


[ANCHoRLiNKS](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#section-links)

# Example headings

## Sample Section

## This'll  be a _Helpful_ Section About the Greek Letter Θ!
A heading containing characters not allowed in fragments, UTF-8 characters, two consecutive spaces between the first and second words, and formatting.

## This heading is not unique in the file

TEXT 1

## This heading is not unique in the file

TEXT 2

# Links to the example headings above

Link to the sample section: [Link Text](#sample-section).

Link to the helpful section: [Link Text](#thisll--be-a-helpful-section-about-the-greek-letter-Θ).

Link to the first non-unique section: [Link Text](#this-heading-is-not-unique-in-the-file).

Link to the second non-unique section: [Link Text](#this-heading-is-not-unique-in-the-file-1).


![Mars HElicopter](https://photojournal.jpl.nasa.gov/archive/PIA25321.gif)
![Curiosity](https://photojournal.jpl.nasa.gov/archive/PIA17938.gif)
![Betty's Rock](https://photojournal.jpl.nasa.gov/jpegMod/PIA25656_modest.jpg)

## Dear_House_of_reps
I have been doing research on the planet mars in public for a bout 4 years. CNN is covering my work and i have trouble eating and communicating. My Family vanished and no Social Security number based resource will aid me. I am struggling with hunger at times and have no shelter. I have women i need to reconnect with to find out what happend. They got kidnapped just b4 covid and tricked me into coming to california, where i was supposed to be headed anyway! And i found out they are victims of a Sex MArket online and the Street Walking and Dancing is just for display. I am complaining about CNN bc Ashley Strickland has no issues communicating from what i see and im stalked and chased by Allied Universal who is the BodyGaurd people of choice of Atlanta's YallyWood and CentralNewsNetwork. I am a native so the girls i was raised to think would be my spouses are up for NBA, Comedy, Film < journalism and everyother industry to deposit semen into. I dont know where my daughter ios from 631 Moreland Ave's illegal eviciton of Rashard Iman Kelly after being denied resources by family services leading to the foprced abduction of Coral Iris Kelly from the home of Copnstancia Arriba. So her i am in Holly wood. I am dating a Popstar named Normani off an on an she plays MineCraft. So thats my side outside. She is really pretty and poses for Vogue but a dark part of her life is that the pictures she takes nude for various publications are used by the local sex trade to keep her marketable for visitors to the city of los angeles and healthy to maintain telepathy for local criminals. She is my best friend(at this level(coral that shit 100bruh)). And since she is mixing with a lot of media i think my blogging gets into the hands of ppl with the power to publish at will. I need balance and a kind cooling center. CNN since we are working to gether can you help me off the streets digitally, can you  help me reconcile my family? Rashard Kelly aka Thaka(Muna Husband, Latto City Erika n nem Husband ) out NasaJPl Mars Mission Address: Jet Propulsion Laboratory, 4800 Oak Grove Dr, Pasadena, CA 91011 [Please Read](https://thakarashard.github.io/ricothaka/dispositionforsherrif)

#TwitterBlock  Screen Recording 2024 08 19 11.55.48 AM <iframe src="https://archive.org/embed/screen-recording-2024-08-19-11.55.48-am" width="640" height="480" frameborder="0" webkitallowfullscreen="true" mozallowfullscreen="true" allowfullscreen></iframe>

[Rashard Kelly injury update offline](https://archive.org/details/vid-20240815-062510) 

<a href="https://ricothaka.github.io/worknotes01"><img src="https://pbs.twimg.com/media/GVJMo0haYAAQRdu?format=jpg&name=large" alt="ricothaka.github.io"> </a>

[RiCOTHAKA.GiTHUB.iO for more](https://ricothaka.github.io/civic01) [CompilingTheBlog=Updated](https://thakarashard.github.io/compiling/dispostionthestory)




Captain America: Chapter 2 - Mechanical Executioner
<iframe src="https://archive.org/embed/captain_america_ep2" width="640" height="480" frameborder="0" webkitallowfullscreen="true" mozallowfullscreen="true" allowfullscreen></iframe>

[The endless possibilities and services LA libraries offer](https://www.cbsnews.com/losangeles/video/the-endless-possibilities-and-services-la-libraries-offer/) <cite>With National Library Week in full swing, a Los Angeles librarian tells us about all of the amazing services they offer to enrich the lives of students, children, and adults.
Apr 11, 2024</cite>

Los angeles is a [Euridite civiliZation](https://en.wiktionary.org/wiki/erudite) so i may need to pay more attention to signage
`characterized by great knowledge; learned or scholarly: an erudite professor; an erudite commentary. Synonyms: sapient, wise, knowledgeable, educated.`

![NasaGLEN_RED_PLANET](https://archive.org/download/C-1997-2554/1997_02554.jpg)
[NAsa_GLeNN PLANET MARS](https://archive.org/details/C-1997-2554)
<cite>creator:"NASA/Glenn Research Center"</cite>
[Glamour Life](https://www.youtube.com/watch?v=1QnOCkQLTC0)
![In my belly](https://science.nasa.gov/wp-content/uploads/2024/03/25792_PIA24548-1200.gif?w=1024&format=webp) im updatig thakarashard.github.io even if i was wrong about plegerism i have to be realistic normani could have seduced me toget e away from california too! So im investigating what got me here waiting outside this porno cess pool, HollywoodFoodCo not normal, and i wonder what exactly active mission means? BC if im confused and being poisoned runing from here to there, ithink Jamie would let me know formerly that i was not a part of nasajpl in anyway bc #Jose_M_Pi ru that shit! an heeee say no! i should have been more humble about working from home... my wife is a slut so... there was a three year old, that family vaporized i wanna come back. I really wanna know if the [Nasa SoundCloud](https://soundcloud.com/nasa) Account is Real
- Rashard...

Perseverance Rover Watches Ingenuity Mars Helicopter’s 54th Flight
<video controls  height="auto" poster="https://d2pn8kiwq2w21t.cloudfront.net/images/PIA25968.width-1320.jpg">

<source src="https://science.nasa.gov/wp-content/uploads/2024/03/6172_PIA25970.mp4" type="video/mp4" />    
<source src="https://science.nasa.gov/wp-content/uploads/2024/03/6172_PIA25970.mp4" type="video/mp4" />
      
Download the
        or
      <a href="https://science.nasa.gov/wp-content/uploads/2024/03/6172_PIA25970.mp4">MP4</a>
        video.
</video>

# Listen to NASA’s Ingenuity Mars Helicopter in Flight
<iframe width="100%" height="300" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/1044556651&color=%238c9265&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/nasa" title="NASA" target="_blank" style="color: #cccccc; text-decoration: none;">NASA</a> · <a href="https://soundcloud.com/nasa/listen-to-nasas-ingenuity-helicopter-as-it-flies-on-mars" title="Listen to NASA’s Ingenuity Mars Helicopter in Flight" target="_blank" style="color: #cccccc; text-decoration: none;">Listen to NASA’s Ingenuity Mars Helicopter in Flight</a></div>
Mars Sounds 




The Landsat 8 & 9 Active Fire and Thermal Anomalies product, generated from the Landsat Operational Land Imager (OLI) shows active fire detections and thermal anomalies, such as volcanoes, and gas flares.
![The_Rover](https://d2pn8kiwq2w21t.cloudfront.net/images/jpegPIA15025.width-1440.jpg)
[Real Bout Fatal Fury 2 - The Newcomers (Korean release)](https://www.retrogames.cc/arcade-games/real-bout-fatal-fury-2-the-newcomers-korean-release.html)
<iframe src="https://archive.org/embed/arcade_garou" width="560" height="384" frameborder="0" webkitallowfullscreen="true" mozallowfullscreen="true" allowfullscreen></iframe>



[What Are Raw Images?](https://solarsystem.nasa.gov/raw-images/what-are-raw-images/)
<cite>[Taken from webpage](https://science.nasa.gov/solar-system/)</cite>
Raw images are photos from space missions that NASA provides online for easy public access in their original (usually monochrome) appearance, largely untouched by image processing software. Raw images, in this context, are generally not the same as truly "raw" science data – meaning the original image data format returned to Earth by spacecraft. They're more like high-quality previews of data received from missions. - [Why NASA offers raw images]() NASA space missions return lots of images to Earth ­– far more than featured images the agency posts on the web and in social media. For example, a long-lived mission like Cassini could return hundreds of thousands of images over its lifetime.

[Rings of Saturn](https://solarsystem.nasa.gov/raw_images/158252/?layout=hds)
![Rings](https://science.nasa.gov/wp-content/uploads/2023/10/W00083940.jpg?w=640&format=webp) 

<div class="container">
  <h1><a href="https://mars.nasa.gov/msl/multimedia/raw-images/?order=sol+desc%2Cinstrument_sort+asc%2Csample_type_sort+asc%2C+date_taken+desc&per_page=50&page=0&mission=msl">Mars Science Laboratory: Curiosity Raw Images</a></h1>

  <div class="gallery-wrap">
    <div class="item item-1"></div>
    <div class="item item-2"></div>
    <div class="item item-3"></div>
    <div class="item item-4"></div>
    <div class="item item-5"></div>
  </div>
 </div>

<div class="social">
  <a href="https://twitter.com/moonlover404" target="_blank">
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/149103/twitter.svg" alt="">
  </a>

</div>

<iframe src="https://archive.org/embed/arcade_rtype2" width="560" height="384" frameborder="0" webkitallowfullscreen="true" mozallowfullscreen="true" allowfullscreen></iframe>


[Compiling WasUpdated](https://thakarashard.github.io/compiling/)
<iframe width="100%" height="300" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/playlists/904236316&color=%2300cbff&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/asiandabratdoll" title="Asian Da Brat" target="_blank" style="color: #cccccc; text-decoration: none;">Asian Da Brat</a> · <a href="https://soundcloud.com/asiandabratdoll/sets/so-icy-princess-1" title="So Icy Princess" target="_blank" style="color: #cccccc; text-decoration: none;">So Icy Princess</a></div>

![Batman](https://upload.wikimedia.org/wikipedia/en/f/f4/Batman1943SerialPoster.jpg) 
Batman is a 1943 American 15-chapter [theatrical serial](https://en.wikipedia.org/wiki/Serial_film) from Columbia Pictures, produced by Rudolph C. Flothow, The serial's story line involves the Batman, a secret U.S. government agent, attempting to defeat the schemes of Japanese agent Dr. Daka operating in Los Angeles at the height of World War II.[3] Serving Daka are his American henchmen.

Batman is notable for being the first appearance on film of Batman and for debuting story elements that quickly became permanent parts of the Batman character's mythos, such as the "Bat's Cave" and its secret entrance through a grandfather clock inside Wayne Manor. The serial also changed the course of how Alfred's physical appearance was depicted in future Batman stories. At the time Batman was released in theaters, Alfred was drawn as a portly gentleman in the comics. Subsequent issues suddenly depicted Alfred as slim and sporting a thin moustache, following actor William Austin's appearance. [Wikipedia](https://en.wikipedia.org/wiki/Batman_(serial))
[Batman 1943 all episodes](https://archive.org/download/batman-1943-episode-01)

<iframe src="https://archive.org/embed/batman-1943-episode-01" width="640" height="480" frameborder="0" webkitallowfullscreen="true" mozallowfullscreen="true" allowfullscreen></iframe>

[uptown butterfly _movie](https://youtu.be/UVhDEN4o7zk?si=c4evez9O4c5Z5SAB) [Tina, @kashdoll so pretty - song](https://youtu.be/-mv0YNUCoj4?si=YE7jtcVRzWUrPwcj) 


[Heltah Skeltah & OGC - Leflaur Leflah Eshkoshka](https://www.youtube.com/watch?v=i4sW3jJuVDg) 

![Muna Ahmed_Memorial](https://pbs.twimg.com/media/GULEQmebcAAhekm?format=jpg&name=large)
[Attack of the Killer Kung-Fu Wolf Bitch](https://boondocks.fandom.com/wiki/Attack_of_the_Killer_Kung-Fu_Wolf_Bitch) 
Robert's online dating adventures lead him to a beautiful woman named Luna, whom he invites for the weekend. Unfortunately, Huey, Riley and Robert soon learn that Luna...[FromFandom](https://boondocks.fandom.com/wiki/Attack_of_the_Killer_Kung-Fu_Wolf_Bitch) [imdb](https://www.imdb.com/title/tt1143232/) [Normani playlist gift](https://youtu.be/wGpJbD9h-J0?si=zaSExbm4087w_yCi) its another cycle bae...



[Watch The Boondocks (Complete Series) on Archive.org](https://archive.org/details/the-boondocks-complete)
[Local TinGz on https://thakarashard.github.io/](https://thakarashard.github.io/civic01)
[Barrington Levy - Under Mi Sensi](https://www.youtube.com/watch?v=uozhx1xeTDg) [Ganja Smuggling - Eek-A-Mouse](https://www.youtube.com/watch?v=UR9Cj5UyVbM) [Bob Marley Tuff Gong Studio Rehearsal 1980 Full session](https://youtu.be/aXIDAd68ThI?si=mUAb-e0AyfKAPdjO) [Nas - Take it in Blood - hiphop](https://youtu.be/pmmnzusZZMU?si=j9p5MfQSv4Wn9YfR) [I Chase the Devil Max Romero](https://www.youtube.com/watch?v=zM4HXY1cLIY)

[JPL and the Space Age: The Hunt for Space Rocks](https://www.youtube.com/watch?v=1wNzTyu36WA) [JPL and the Space Age: Landing on Mars](https://youtu.be/7aKewWHXXRE?si=MouyInZGPsjt8Yw6) 
[Hubble Space Telescope, Planet 9, Curiosity Mars Rover, Cosmic Roulette  60 Minutes Full Episodes](https://youtu.be/ZYlALC1Pmv4?si=0GnKqpjKQmyYaxFw) 
[Inside SpaceX's Mission to Send Humans into Deep Space  Foreign Correspondent](https://youtu.be/qInkR8P7q3M?si=uG4WNpxUxhCW0Igj) 
[Mars Direct 3  A Proposal for SpaceX's Mars Program  Miguel Gurrea](https://youtu.be/YA7YQcA9Waw?si=LTJHZDvY65gHNnjG)
 [JPL and the Space Age: The Changing Face of Mars](https://www.youtube.com/watch?v=eaSaVanPysA)
  [Why Does NASA Want to Explore Jupiter’s Ocean Moon? (Europa Clipper Science Overview)](https://youtu.be/GXMA-04CADw?si=L9-7PuPzn1ysh5jN)
   [NASA's Breathtaking Findings on Ganymede: Exploring the Marvels of Jupiter's Largest Moon](https://youtu.be/s94XNsypTeo?si=YmvkYYiem5DdPAQo)
    [NASA's Next-Generation Solar Sail Mission](https://youtu.be/rfYLnbw7iu8?si=hcTrcU6zOGLUyHgx)


Androiding 
[Smart Phone Screenshare](https://archive.org/details/screen-20240731-050451_202408)

[Fraggle Rock: The Animated Series](https://archive.org/details/fraggle-toon) [Fraggle Rock](https://archive.org/details/MashSeries) [Robo Cop The Complete Series](https://archive.org/details/RoboCopTheCompleteSeries) [Fraggle Rock UK (Rare Episodes)](https://archive.org/details/fraggle-rock-uk)




![curiosity](https://mars.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/04258/opgs/edr/ncam/NRB_775492033EDR_S1080792NCAM00594M_.JPG)
[Front_Left_Hazcam:Two_Year_Movie](https://science.nasa.gov/resource/front-left-hazcam-two-year-movie/)

<video controls  height="auto" poster="https://science.nasa.gov/wp-content/uploads/2024/03/48025_FRHTwoYearMovie.gif">

<source src="https://science.nasa.gov/wp-content/uploads/2024/03/20230217FrontLeftHazcamTwoYearMovie-1280.mp4" type="video/mp4" />    
<source src="https://github.com/ricoThaka/ricothaka.github.io/raw/master/assets/PerseveranceTwoYearMovie.mp4" type="video/mp4" />
      
        Download the
        or
        <a href="">MP4</a>
        video.
</video>


![perserverance](https://mars.nasa.gov/mars2020-raw-images/pub/ods/surface/sol/00297/ids/edr/browse/zcam/ZR0_0297_0693322301_098ECM_N0090000ZCAM01012_026050J01_1200.jpg)
https://mars.nasa.gov/mars2020/multimedia/raw-images/ZR0_0297_0693322301_098ECM_N0090000ZCAM01012_026050J
[International Space Station Operations (June 28, 2024)](https://www.youtube.com/live/u-BGAPuzxZU?si=9TTR6kH--bpQE5c3)
[Perseverance Rover's Descent and Touchdown on Mars](https://svs.gsfc.nasa.gov/31250) 
[Perseverance Rover’s Descent and Touchdown on Mars: Onboard Camera Views](https://science.nasa.gov/wp-content/uploads/2024/03/45703_JPL-20210222-M2020f-0001-Perseverance_Rovers_Descent_and_Touchdown_on_Mars-1.mp4)

>NASA's Mars 2020 Perseverance mission captured thrilling footage of its rover landing in Mars' Jezero Crater on Feb. 18, 2021. The real footage in this video was captured by several cameras that are part of the rover's entry, descent, and landing suite. The views include a camera looking down from the spacecraft's descent stage (a kind of rocket-powered jet pack that helps fly the rover to its landing site), a camera on the rover looking up at the descent stage, a camera on the top of the aeroshell (a capsule protecting the rover) looking up at that parachute, and a camera on the bottom of the rover looking down at the Martian surface.

<video controls width="100%" height="auto" poster="https://www.nasa.gov/wp-content/uploads/2021/06/pia24542-perseverances-selfie-with-ingenuity-1041.jpg">
    
<source src="https://svs.gsfc.nasa.gov/vis/a030000/a031200/a031250/Perseverance-landing-1080p.mp4" type="video/mp4" />
         Download the
        or
<a href="https://svs.gsfc.nasa.gov/vis/a030000/a031200/a031250/Perseverance-landing-1080p.mp4">MP4</a>
        video.
</video>    

[15 Second Clip of Parachute Deployment(MP4) (18.86 MB)](https://science.nasa.gov/wp-content/uploads/2024/03/45732_nasa_perseverance_parachute_deployment.mp4)

[Rashards Archive Uploads](https://archive.org/details/@thakaserika_selassie_kelly)




[Play Retro SNK Neo Geo games online | NEOGEOFUN](https://www.neogeofun.com/)
[Marvel Super Heroes Vs Street Fighter (970625 USA)](https://www.retrogames.cc/arcade-games/marvel-super-heroes-vs-street-fighter-970625-usa.html#)

[Screen Recording 2024 07 29 4.53.08 PM](https://archive.org/details/screen-recording-2024-07-29-4.53.08-pm)





![MEGADRiVE](https://upload.wikimedia.org/wikipedia/commons/f/fd/JP_MegaDrive_Logo.gif)

[Sonic the Hedgehog Rev 1](https://archive.org/details/sg_Sonic_the_Hedgehog_Rev_1_1991_Sega_JP-KR_en)
Sonic the Hedgehog (ソニック・ザ・ヘッジホッグ Sonikku za Hejjihoggu?) is a platform video game developed by Sonic Team and published by Sega for the Sega Mega Drive/Genesis. First released in North America, Europe, and Australia on June 23, 1991, the game is the first installment in the Sonic the Hedgehog series 



![Sonic1 Not For Resale](https://www.lifewire.com/thmb/8ncd0X34c6dglK5uEdM60asZn8Y=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/Sonic_the_Hedgehog_Coverart-4-5b958f8ac9e77c0082ee596c.jpg)" 








![linkedin](https://pbs.twimg.com/media/GILuiVmbEAAyRtH?format=jpg&name=large)

















[Contact](https://youtu.be/oG6y0mmI0N4?si=dPt23E0Ky8dxleUV) "We are not alone..." Two-time Academy Award-winner Jodie Foster and Hollywood's brightest new star, Matthew McConaughey, shine in this spellbinding drama of a dedicated astronomer's quest to make first Contact. Despite scorn from her colleagues...[imdb](https://www.imdb.com/title/tt0118884/) 



    











[back](./)
