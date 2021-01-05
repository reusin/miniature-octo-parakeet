<h3>Sample CRUD Application Setup</h3>

<p>For convenience sake, a sample nodejs application demonstrating the Basic CRUD operations of redis database is available in <a href="https://github.com/snippet-java/nodejs-redis-api-example.git">this repository</a>. The following section deals with connecting the redis database previously exposed as a kubernetes service, to the nodejs application</p>

<h3>1. Create a new directory</h3>
<pre><code>
mkdir redis
</code></pre>

<h3>2. Clone the git repository</h3>
<pre><code>
git clone https://github.com/snippet-java/nodejs-redis-api-example.git
</code></pre>

<h3>3. Modify configuration file</h3>
<p>Connection to a redis database requires the <b>hostname</b>, <b>port</b> and <b>password</b>, which must be supplied to the redis connection client in the application. The connection code can be found inside <i>app.js</i> and looks as such</p>
<pre><code>
var client = redis.createClient(port, hostname, {no_ready_check: true});
client.auth(password)
</pre></code>
<p>Navigate to the directory which contains the application code</p>
<pre><code>
$ cd nodejs-redis-api-example
</pre></code>
<p>For this application, the configuration for connecting to Redis is accepted through the <i>sevices.json</i> file. Let's view the contents of the <i>services.json</i></p>
<pre><code>
$ cat services.json
{
        "redis" : {
                "hostname": "",
                "password": "",
                "port": ""
        }
}
</code></pre>
<p>Replace the hostname, password and port in <i>services.json</i></p> file.
<pre><code>
cat <<EOF> services.json
{
        "redis" : {
                "hostname": "$(127.0.0.1)",
                "password": "$(REDIS_PASSWORD)",
                "port": "30001"
        }
}
</code></pre>

<h3>4. Run the Application</h3>
<p>Install node package dependencies</p>
<pre><code>
npm install
</pre></code>
<p>Run the node application</p>
<pre><code>
$ node app.js
Express server listening on port 3000
Connected to Redis
node_redis: Warning: Redis server does not require a password, but a password was supplied.
</pre></code>
