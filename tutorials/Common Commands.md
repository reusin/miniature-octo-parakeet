<h2>A few sample commands</h2>

<p>Redis allows atomic operations on the datstructures stored, like appending to a string; incrementing the value in a hash; pushing an element to a list; computing set intersection, union and difference; or getting the member with highest ranking in a sorted set. The following section will provide instructions to perform a few simple commands</p>

<h3>Set Operation </h3>
<p>Command Pattern: <code>SET key value</code></p>
<p>This sets a key to hold the string value. If key already holds a value, it is overwritten, regardless of its type. </p>

<p>In this example, the string value <i>"John Doe"</i> is mapped to the key, <i>name</i></p>
<pre>
<code>
redis> SET name "John Doe"
OK
redis> GET name
"John Doe"
</code></pre>

<h3>Get value which is mapped to Key</h3>
<p>Command Pattern: <code>GET key</code></p>
<p>Get the value of key. If the key does not exist the special value nil is returned. An error is returned if the value stored at key is not a string, because GET only handles string values</p>
<pre><code>
redis> GET nonexisting
(nil)
redis> SET mykey "Hello"
"OK"
redis> GET mykey
"Hello"
</code></pre>

<h3>Set Mulitple Key Values</h3>
<p>Command Pattern: <code>MSET key value [key value ...]</code></p>
<p>Unlike SET, MSET can set multiple keys to their respective values. MSET replaces existing values with new values, just as regular SET. MSET is atomic, so all given keys are set at once. It is not possible for clients to see that some of the keys were updated while others are unchanged.</p>

<p>In this example, multiple keys are mapped to their respective values</p>
<pre>
<code>
redis> MSET key1 "Hello" key2 "World"
OK
redis> GET key1
"Hello"
</code></pre>

<h3>Get Values which are mapped to multiple keys</h3>
<p>Command Pattern: <code>MGET key [key ...]</code></p>
<p>Returns the values of all specified keys. For every key that does not hold a string value or does not exist, the special value nil is returned. Because of this, the operation never fails.</p>

<h3>Set fields in hash stored as key</h3>
</p>Command Patten: <code>HSET key field value [field value ...]</code></p>
<p>Sets field in the hash stored at key to value. If key does not exist, a new key holding a hash is created. If field already exists in the hash, it is overwritten.</p>
<p>Note: As of Redis 4.0.0, HSET is variadic and allows for multiple field/value pairs.</p>

<pre><code>
redis> HSET myhash field1 "Hello"
(integer) 1
redis> HGET myhash field1
"Hello"
</code></pre>

<h3>Get field value of hash stored as key</h3>
<p>Command pattern: <code>HGET key field</code></p>
<p>The fields set in hash stored at key can be retrieved using HGET</p>
<pre><code>
redis> HSET myhash field1 "foo"
(integer) 1
redis> HGET myhash field1
"foo"
redis> HGET myhash field2
(nil)
redis> 
</code></pre>

<h3>Get Multiple field value of hash stored as key</h3>
<p>Command Pattern: <code>HMGET key field [field ...]</code></p>
<p>Returns the values associated with the specified fields in the hash stored at key. For every field that does not exist in the hash, a nil value is returned. Because non-existing keys are treated as empty hashes, running HMGET against a non-existing key will return a list of nil values.</p>

<pre><code>
redis> HSET myhash field1 "Hello"
(integer) 1
redis> HSET myhash field2 "World"
(integer) 1
redis> HMGET myhash field1 field2 nofield
1) "Hello"
2) "World"
3) (nil)
</code></pre>

<h3>Reference</h3>
<a href="https://redis.io/commands">Redis Documentation</a>
