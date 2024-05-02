
# HDEV SMS GATEWAY

### HDEV SMS. MIT license.

Use from a PHP script:


# INitiate sms
```php
include 'sms_parse.php';

//SEND SMS

hdev_sms::api_id("Your Api ID");
hdev_sms::api_key("Your Api Key");
$msg = hdev_sms::send("SENDER ID","TELL","MESSAGE");

var_dump($msg);//to get sms server response
```

# TOP UP/ Add amount to account 
```php
include 'sms_parse.php';

//TOP UP

hdev_sms::api_id("Your Api ID");
hdev_sms::api_key("Your Api Key");
$result = hdev_sms::topup($tel,$amount);

var_dump($result);//to get sms server response
```

*All of our response are objects for example to access the status in response you use
```php
	$status = $result->status;
```

# For Python

```python
import requests
# Replace _your_api_ID_ with your actual API ID 
# Replace _your_api_Key_ with your actual API KEY
url = "https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_"

payload = {'sender_id': '_your_sender_id_', #Your assigned sender id
'ref': 'sms', # This field remain uncganged as it identifies the service you need
'message': 'This Is Test Message', # Your Message
'tel': '_receiver_tel_'} # Telephone number
files=[

]

headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)

```

# For C#
```c#
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_");
var content = new MultipartFormDataContent();
content.Add(new StringContent("_your_sender_id_"), "sender_id");
content.Add(new StringContent("sms"), "ref");
content.Add(new StringContent("This Is Test Message"), "message");
content.Add(new StringContent("_receiver_tel_"), "tel");
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

# For JAVA
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = new MultipartBody.Builder().setType(MultipartBody.FORM)
  .addFormDataPart("sender_id","_your_sender_id_")
  .addFormDataPart("ref","sms")
  .addFormDataPart("message","This Is Test Message")
  .addFormDataPart("tel","_receiver_tel_")
  .build();
Request request = new Request.Builder()
  .url("https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_")
  .method("POST", body)
  .build();
Response response = client.newCall(request).execute();
```

# For GO
```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("sender_id", "_your_sender_id_")
  _ = writer.WriteField("ref", "sms")
  _ = writer.WriteField("message", "This Is Test Message")
  _ = writer.WriteField("tel", "_receiver_tel_")
  err := writer.Close()
  if err != nil {
    fmt.Println(err)
    return
  }


  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

# For RUBY 
```ruby
require "uri"
require "net/http"

url = URI("https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
form_data = [['sender_id', '_your_sender_id_'],['ref', 'sms'],['message', 'This Is Test Message'],['tel', '_receiver_tel_']]
request.set_form form_data, 'multipart/form-data'
response = https.request(request)
puts response.read_body
```

# For Javascript - jquery
```javascript
var form = new FormData();
form.append("sender_id", "_your_sender_id_");
form.append("ref", "sms");
form.append("message", "This Is Test Message");
form.append("tel", "_receiver_tel_");

var settings = {
  "url": "https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_",
  "method": "POST",
  "timeout": 0,
  "processData": false,
  "mimeType": "multipart/form-data",
  "contentType": false,
  "data": form
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

# For Kotlin
```kotlin
val client = OkHttpClient()
val mediaType = "text/plain".toMediaType()
val body = MultipartBody.Builder().setType(MultipartBody.FORM)
  .addFormDataPart("sender_id","_your_sender_id_")
  .addFormDataPart("ref","sms")
  .addFormDataPart("message","This Is Test Message")
  .addFormDataPart("tel","_receiver_tel_")
  .build()
val request = Request.Builder()
  .url("https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_")
  .post(body)
  .build()
val response = client.newCall(request).execute()
```

# For NodeJs
```javascript
const axios = require('axios');
const FormData = require('form-data');
let data = new FormData();
data.append('sender_id', '_your_sender_id_');
data.append('ref', 'sms');
data.append('message', 'This Is Test Message');
data.append('tel', '_receiver_tel_');

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://sms-api.hdev.rw/v1/api/_your_api_ID_/_your_api_Key_',
  headers: { 
    ...data.getHeaders()
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});
```

