

# Module ersip_trans #
* [Data Types](#types)
* [Function Index](#index)
* [Function Details](#functions)

<a name="types"></a>

## Data Types ##




### <a name="type-event_received">event_received()</a> ###


<pre><code>
event_received() = {received, <a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>}
</code></pre>

 Message generated by transaction user is ready to send:



### <a name="type-event_send">event_send()</a> ###


<pre><code>
event_send() = {send, <a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>}
</code></pre>




### <a name="type-event_timer">event_timer()</a> ###


<pre><code>
event_timer() = term()
</code></pre>

 Message matching transaction is received.



### <a name="type-result">result()</a> ###


<pre><code>
result() = {<a href="#type-trans">trans()</a>, [<a href="ersip_trans_se.md#type-effect">ersip_trans_se:effect()</a>]}
</code></pre>




### <a name="type-tid">tid()</a> ###


<pre><code>
tid() = <a href="ersip_trans_id.md#type-transaction_id">ersip_trans_id:transaction_id()</a>
</code></pre>




### <a name="type-trans">trans()</a> ###


<pre><code>
trans() = #trans{id = <a href="ersip_trans.md#type-tid">ersip_trans:tid()</a>, module = ersip_trans_client | ersip_trans_server, instance = <a href="#type-trans_instance">trans_instance()</a>}
</code></pre>




### <a name="type-trans_event">trans_event()</a> ###


<pre><code>
trans_event() = <a href="#type-event_timer">event_timer()</a> | <a href="#type-event_received">event_received()</a> | <a href="#type-event_send">event_send()</a>
</code></pre>




### <a name="type-trans_instance">trans_instance()</a> ###


<pre><code>
trans_instance() = <a href="ersip_trans_client.md#type-trans_client">ersip_trans_client:trans_client()</a> | <a href="ersip_trans_server.md#type-trans_server">ersip_trans_server:trans_server()</a>
</code></pre>

<a name="index"></a>

## Function Index ##


<table width="100%" border="1" cellspacing="0" cellpadding="2" summary="function index"><tr><td valign="top"><a href="#client_id-1">client_id/1</a></td><td>Create client transaction identifier by filled outgoint
request.</td></tr><tr><td valign="top"><a href="#client_id-2">client_id/2</a></td><td>Create client transaction id by response and trimmed topmost
via.</td></tr><tr><td valign="top"><a href="#event-2">event/2</a></td><td></td></tr><tr><td valign="top"><a href="#has_final_response-1">has_final_response/1</a></td><td>Final response has been sent or received.</td></tr><tr><td valign="top"><a href="#id-1">id/1</a></td><td></td></tr><tr><td valign="top"><a href="#new_client-2">new_client/2</a></td><td></td></tr><tr><td valign="top"><a href="#new_server-2">new_server/2</a></td><td>Create server transaction by message.</td></tr><tr><td valign="top"><a href="#server_cancel_id-1">server_cancel_id/1</a></td><td>Create transaction id of cancelled INVITE request by CANCEL SIP
message.</td></tr><tr><td valign="top"><a href="#server_id-1">server_id/1</a></td><td>Create server transaction identifier by incoming request.</td></tr><tr><td valign="top"><a href="#validate-1">validate/1</a></td><td>Parse all required headers to use sipmsg in transaction.</td></tr></table>


<a name="functions"></a>

## Function Details ##

<a name="client_id-1"></a>

### client_id/1 ###

<pre><code>
client_id(OutReq::<a href="ersip_request.md#type-request">ersip_request:request()</a>) -&gt; <a href="#type-tid">tid()</a>
</code></pre>
<br />

Create client transaction identifier by filled outgoint
request.

<a name="client_id-2"></a>

### client_id/2 ###

<pre><code>
client_id(RecvVia::<a href="ersip_hdr_via.md#type-via">ersip_hdr_via:via()</a>, SipMsg::<a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>) -&gt; <a href="#type-tid">tid()</a>
</code></pre>
<br />

Create client transaction id by response and trimmed topmost
via

<a name="event-2"></a>

### event/2 ###

<pre><code>
event(Event::<a href="#type-trans_event">trans_event()</a>, Trans::<a href="#type-trans">trans()</a>) -&gt; <a href="#type-result">result()</a>
</code></pre>
<br />

<a name="has_final_response-1"></a>

### has_final_response/1 ###

<pre><code>
has_final_response(Trans::<a href="#type-trans">trans()</a>) -&gt; boolean()
</code></pre>
<br />

Final response has been sent or received.

<a name="id-1"></a>

### id/1 ###

<pre><code>
id(Trans::<a href="#type-trans">trans()</a>) -&gt; <a href="#type-tid">tid()</a>
</code></pre>
<br />

<a name="new_client-2"></a>

### new_client/2 ###

<pre><code>
new_client(OutReq::<a href="ersip_request.md#type-request">ersip_request:request()</a>, Options::<a href="ersip.md#type-sip_options">ersip:sip_options()</a>) -&gt; <a href="#type-result">result()</a>
</code></pre>
<br />

<a name="new_server-2"></a>

### new_server/2 ###

<pre><code>
new_server(SipMsg::<a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>, Options::<a href="ersip.md#type-sip_options">ersip:sip_options()</a>) -&gt; <a href="#type-result">result()</a>
</code></pre>
<br />

Create server transaction by message.

<a name="server_cancel_id-1"></a>

### server_cancel_id/1 ###

<pre><code>
server_cancel_id(CancelSipMsg::<a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>) -&gt; <a href="#type-tid">tid()</a>
</code></pre>
<br />

Create transaction id of cancelled INVITE request by CANCEL SIP
message.

<a name="server_id-1"></a>

### server_id/1 ###

<pre><code>
server_id(InSipMsg::<a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>) -&gt; <a href="#type-tid">tid()</a>
</code></pre>
<br />

Create server transaction identifier by incoming request.

<a name="validate-1"></a>

### validate/1 ###

<pre><code>
validate(SipMsg::<a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>) -&gt; Result
</code></pre>

<ul class="definitions"><li><code>Result = {ok, <a href="ersip_sipmsg.md#type-sipmsg">ersip_sipmsg:sipmsg()</a>} | {error, term()}</code></li></ul>

Parse all required headers to use sipmsg in transaction.
