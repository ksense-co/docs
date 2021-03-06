# Subscription Services

Following page contains best practices and guidelines for subscription services. In order to get maximum insights from data please follow those guidelines as close as possible

### Events

Following [events](../events-api/) should be exported:

| Event Type | Importance | Comment |
| :--- | :--- | :--- |
| pv | MEDIUM | [JavaScript API](../events-api/javascript-pixel.md) is recommended. Sending pv events will increase insights quality |
| subscribed | MANDATORY | [Server API ](../events-api/server-api.md)is recommended |
| unsubscribed | MANDATORY | [Server API ](../events-api/server-api.md)is recommended |
| sub\_pause | MEDIUM | [Server API ](../events-api/server-api.md)is recommended. It's possible to replace this call with unsubscribe event. |
| sub\_resume | MEDIUM | [Server API ](../events-api/server-api.md)is recommended. It's possible to replace this call with subscribe event. |
| support\_contact | MEDIUM | [Server API ](../events-api/server-api.md)is recommended. |
| user\_info | MANDATORY | [Server API ](../events-api/server-api.md)is recommended. |

### User ID

kSense provides multiple ways of user identification. However, for achieving better results it's crucial to pick one user identification approach and use it in every event type. Recommended ways are:

* **email**. You can use encryption \(enc1 is preferred\)
* **phone.** The same as e-mail
* **internal\_id.** Less reliable way

### Event requests example

Use [https://p.ksense.ai/api/v2/post\_event](../events-api/server-api.md) calls with Event JSON as a body

**Basic events**

{% tabs %}
{% tab title="subscribed" %}
```javascript
{
  "time": "2018-11-12 14:02:45",
  "type": "subscribed",
  "event_id": "{unique event id, can be random string}",
  "data_source_id": "{your datasource id}",
  "user_id": {
    "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",
  }
}
```
{% endtab %}

{% tab title="unsubscribed" %}
```javascript
{
  "time": "2018-11-12 14:02:45",
  "type": "unsubscribed",
  "event_id": "{unique event id, can be random string}",
  "data_source_id": "{your datasource id}",
  "user_id": {
    "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",
  }
}
```
{% endtab %}

{% tab title="sub\_pause" %}
```javascript
{
  "time": "2018-11-12 14:02:45",
  "type": "sub_pause",
  "event_id": "{unique event id, can be random string}",
  "data_source_id": "{your datasource id}",
  "user_id": {
    "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",
  }
}
```
{% endtab %}

{% tab title="sub\_resume" %}
```javascript
{
  "time": "2018-11-12 14:02:45",
  "type": "sub_resume",
  "event_id": "{unique event id, can be random string}",
  "data_source_id": "{your datasource id}",
  "user_id": {
    "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",
  }
}
```
{% endtab %}
{% endtabs %}

#### Supplemental events

{% tabs %}
{% tab title="user\_info" %}


```javascript
{
    "type": "user_info",
    "data_source_id": "{data source id}",
    "user_id": {
        "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",
    },
    "event_data": {
        "zip": 10016,
        "value_currency": "USD",
        "address_line_2": "apt 345",
        "acquisition_channel": ["online", "facebook"]
    }
}
```

 
{% endtab %}

{% tab title="support\_contact" %}


```javascript
{
  "time": "2018-11-12 14:02:45",
  "type": "support_contact",
  "event_id": "{unique event id, can be random string}",
  "data_source_id": "{your datasource id}"
}
```
{% endtab %}
{% endtabs %}

