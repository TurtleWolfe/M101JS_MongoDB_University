
     ,-----.,--.                  ,--. ,---.   ,--.,------.  ,------.
    '  .--./|  | ,---. ,--.,--. ,-|  || o   \  |  ||  .-.  \ |  .---'
    |  |    |  || .-. ||  ||  |' .-. |`..'  |  |  ||  |  \  :|  `--, 
    '  '--'\|  |' '-' ''  ''  '\ `-' | .'  /   |  ||  '--'  /|  `---.
     `-----'`--' `---'  `----'  `---'  `--'    `--'`-------' `------'
    ----------------------------------------------------------------- 
 
<h3>Installing MongoDB on a Cloud9 workspace</h3>

<p>To install MongoDB in your workspace open a terminal and run the following command:</p>

<p></p><pre><code class="hljs cs">sudo apt-<span class="hljs-keyword">get</span> install -y mongodb-org</code></pre>

<h3>Running MongoDB on a Cloud9 workspace</h3>

<p>To run MongoDB, run the following below (passing the correct parameters to it). Mongodb data will be stored in the folder <code>data</code>.</p>

<p></p><pre><code class="hljs ruby">mkdir data
echo <span class="hljs-string">'mongod --bind_ip=$IP --dbpath=data --nojournal --rest "$@"'</span> &gt; mongod
chmod a+x mongod</code></pre>

<p>You can start mongodb by running the <code>mongod</code> script on your project root:</p>

<p></p><pre><code class="hljs ruby">./mongod</code></pre>

<h2>MongoDB parameters used:</h2>

<p><code>--dbpath=data</code> - Because it defaults to <code>/var/db</code> (which isn't accessible)<br><code>--nojournal</code> - mongodb usually pre-allocates 2 GB journal file  
(which exceeds Cloud9 disk space quota)<br><code>--bind_ip=$IP</code> - Because you can't bind to 0.0.0.0<br><code>--rest</code> - Runs on default port 28017</p>

<h1>Drivers</h1>

<p>You should use the host <code>$IP</code> instead of <code>localhost</code> as your driver connection URL. For example, in Node, it is: <code>process.env.IP</code></p>

<h1>Shell Access</h1>

<p>To access a shell prompt for the above MongoDB run the following.</p>

<p></p><pre><code class="hljs ruby">$ mongo</code></pre>

<p>Check out <a href="http://docs.mongodb.org/manual/reference/mongo-shell/" rel="nofollow">docs.mongodb.org<span class="badge badge-notification clicks" title="825 clicks">825</span></a> for details on how to use the shell</p></div>

HomeWork 1.1  
__Run `mongorestore` from the system command line, not the mongo shell.__  

Now, using the Mongo shell, perform a find() on the collection called hw1_1 in the database m101. There is one document in this collection. Please provide the value corresponding to the "answer" key (without the surrounding quotes) from the document returned.

[MongoDB University Wk 1 Intro part 1](https://www.twitch.tv/videos/217252887 "1 hour")  
57:50     mongorestore dump  

[MongoDB University Wk 1 Intro part 2](https://www.twitch.tv/videos/217255411 "hour and a half")  
05:40     help  

        db.help()                    help on db methods
        db.mycoll.help()             help on collection methods
        sh.help()                    sharding helpers
        rs.help()                    replica set helpers
        help admin                   administrative help
        help connect                 connecting to a db help
        help keys                    key shortcuts
        help misc                    misc things to know
        help mr                      mapreduce

        show dbs                     show database names
        show collections             show collections in current database
        show users                   show users in current database
        show profile                 show most recent system.profile entries with time >= 1ms
        show logs                    show the accessible logger names
        show log [name]              prints out the last segment of log in memory, 'global' is default
        use <db_name>                set current database
        db.foo.find()                list objects in collection foo
        db.foo.find( { a : 1 } )     list objects in foo where a == 1
        it                           result of the last line evaluated; use to further iterate
        DBQuery.shellBatchSize = x   set default number of items to display on shell
        exit                         quit the mongo shell


#####     06:00     moved hm1-1 to root 
09:25     show dbs  
09:45     use m101  
09:52     show collections  
11:36     db.hw1_1.find()

#####     14:00     moved hm1-2 to root  
15:05     mongorestore dump  
16:00     use m101  
16:04     show collections  
17:51     npm install  
18:37     node app.js  

#####     14:00     moved hm1-3 to root  
15:05     mongorestore dump  
16:00     use m101  
16:04     show collections  
17:51     npm install  
18:37     node app.js  





[MongoDB University Wk 2 Intro part 1](https://www.twitch.tv/videos/217252887 "1 hour")  
#####     HomeWork 2.1  
57:50   `db.movieDetails.find().count()`  
57:50   __`db.movieDetails.find({ year: 2013, rated: "PG-13", "awards.wins": 0 }).pretty()`__  
?year 2013 that is rated PG-13 and won no awards.  

#####     HomeWork 2.2  
57:50   `db.movieDetails.find({year: 1964}, {title: 1, _id: 0})`  
NOTE: We are not asking you to consider specifically which documents would be output from the queries below, but rather what fields the output documents would contain.  

#####     HomeWork 2.3  
57:50   `db.movieDetails.find({"countries.1": "Sweden"}, {title: 1, _id: 0})`  
Using the video.movieDetails collection, how many movies list "Sweden" second in the the list of countries.  

#####     HomeWork 2.4  
57:50   `db.movieDetails.find({"genres": ["Comedy", "Crime"] }, { title: 1, genres: 1, _id: 0 })`  
How many documents in our video.movieDetails collection list just the two genres: "Comedy" and "Crime" with "Comedy" listed first.  

#####     HomeWork 2.5  
`db.movieDetails.find( { $and: [ { genres: "Comedy" }, { genres: "Crime" } ] } , { title: 1, genres: 1, _id: 0 } ).count()`  
How many documents in the video.movieDetails collection list both "Comedy" and "Crime" as genres regardless of how many other genres are listed?  

watch some training videos at  
http://www.youtube.com/user/c9ide.  

Happy coding!  
TurtleWolfe.com
