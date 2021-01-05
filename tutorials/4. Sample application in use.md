<h3>CRUD operations in the node.js application</h3>

<h3>Setting a key</h3>
<p>Query Pattern: <code>curl <<a>URL>/redis/set?key=value</code></p>
<pre><code>
$ curl 127.0.0.1:3000/redis/set?name=Doe
{
  "data": "OK"
}
</pre></code>

<h3>Getting a key</h3>
<p>Query Pattern: <code>curl <<a>URL>/redis/get?key=abc </code></p>
<pre><code>
$ curl 127.0.0.1:3000/redis/get?key=name
{
  "data": "Doe"
}
</pre></code>

<h3>Deleting a key</h3>
<p>Query Pattern: <code>curl <<a>URL>/redis/del?key=abc</code></p>
<pre><code>
$ curl 127.0.0.1:3000/redis/del?key=name
{
  "data": 1
}
</pre></code>

<h3>Get All Keys</h3>
<p>Query Pattern: <code>curl <<a>URL>/redis/keys</code></p>
<pre><code>
$ curl 127.0.0.1:3000/redis/keys
{
  "data": [
    "name"
  ]
}
</pre></code>

<h3>Delete all Keys</h3>
<p>Query Pattern: <code>curl <<a>URL>/redis/flushdb</code></p>
<pre><code>
$ curl 127.0.0.1:3000/redis/flushdb    
{
  "data": 1
}
</pre></code>
