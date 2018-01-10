
     ,-----.,--.                  ,--. ,---.   ,--.,------.  ,------.
    '  .--./|  | ,---. ,--.,--. ,-|  || o   \  |  ||  .-.  \ |  .---'
    |  |    |  || .-. ||  ||  |' .-. |`..'  |  |  ||  |  \  :|  `--, 
    '  '--'\|  |' '-' ''  ''  '\ `-' | .'  /   |  ||  '--'  /|  `---.
     `-----'`--' `---'  `----'  `---'  `--'    `--'`-------' `------'
    ----------------------------------------------------------------- 


export NODE_PATH=$NODE_PATH:/home/ubuntu/.nvm/versions/node/v6.11.2/lib/node_modules  
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
Run mongorestore from the system command line, not the mongo shell.  

Now, using the Mongo shell, perform a find() on the collection called hw1_1 in the database m101. There is one document in this collection. Please provide the value corresponding to the "answer" key (without the surrounding quotes) from the document returned.


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


watch some training videos at  
http://www.youtube.com/user/c9ide.  

Happy coding!  
TurtleWolfe.com