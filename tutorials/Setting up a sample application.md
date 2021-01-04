<h3>Sample CRUD Application Setup</h3>

<h3>1. Create a new directory</h3>
<pre><code>
mkdir redis
</code></pre>

<h3>2. Clone the git repository</h3>
<pre><code>
git clone https://github.com/snippet-java/nodejs-redis-api-example.git
</code></pre>

<h3>3. Modify configuration file</h3>
<p>Navigate to the directory which contains the application code</p>
<pre><code>
$ cd nodejs-redis-api-example
</pre></code>
<p>The configuration for connecting to Redis is present in the sevices.json file. Let's view the contents of the <i>services.json</i></p>
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
<p>Replace the hostname, password and port in <i>services</i>.json</p>
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
