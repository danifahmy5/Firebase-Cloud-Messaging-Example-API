# Request FCM Google
Firebase Cloud Messaging (FCM) adalah layanan push notification yang ditawarkan oleh Google. Project ini memberikan contoh bagaimana mengirim notifikasi menggunakan request HTTP ke FCM.

## Fitur
- Mengirim notifikasi melalui request HTTP
- Dapat mengirim notifikasi ke satu atau beberapa perangkat

## Requirements
- API Key dari Firebase Console

## Struktur Body JSON

Berikut adalah contoh lengkap dari struktur body JSON yang dapat digunakan untuk mengirim notifikasi menggunakan FCM:

```
{
   "to" : "device_token",
   "collapse_key" : "type_a",
   "notification" : {
      "body" : "Body of Your Notification",
      "title": "Title of Your Notification",
      "icon" : "notification_icon",
      "sound" : "default"
   },
   "data" : {
      "key1" : "value1",
      "key2" : "value2"
   }
}
```

Berikut adalah penjelasan dari setiap elemen di body JSON:

- `to`: Merupakan token perangkat yang menerima notifikasi. Anda dapat menentukan token perangkat tertentu atau grup perangkat menggunakan topic.
- `collapse_key`: Merupakan kunci yang digunakan untuk mengirimkan notifikasi hanya satu kali dalam jangka waktu tertentu, meskipun beberapa permintaan diterima dalam jangka waktu tersebut.
- `notification`: Merupakan objek JSON yang menentukan konten notifikasi, seperti judul, pesan, ikon, dan suara.
- `data`: Merupakan objek JSON yang menentukan data tambahan yang akan diterima pada aplikasi saat notifikasi diterima.
Catatan: Dalam payload JSON, Anda juga dapat menggunakan elemen `registration_ids` ketika ingin mengirim notifikasi ke beberapa perangkat sekaligus.


## API Reference

#### Send Messaging

```http
  POST https://fcm.googleapis.com/fcm/send
```

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. API Key dari Firebase Console | 
| `Content-Type` | `application/json` | **Optional**. Data Type | 
| `Accept` | `application/json` | **Optional**. Data Type | 


## Contoh 

dengan PHP Guzzle

```bash
$client = new Client();
$headers = [
  'Authorization' => 'key=<YOUR_API_KEY>',
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
];
$body = '{
  "to": "<TOKEN_DEVICE>",
  "collapse_key": "type_a",
  "priority": "high",
  "notification": {
    "android_channel_id": "",
    "title": "Test notifikasi",
    "body": "body notifikasi",
    "sound": "default",
    "color": "#005f73"
  }
}';

$request = new Request('POST', 'https://fcm.googleapis.com/fcm/send', $headers, $body);
$res = $client->sendAsync($request)->wait();
echo $res->getBody();


```


## Dokumentasi

Lihat dokumentasi resmi Firebase Cloud Messaging untuk informasi lebih lanjut mengenai bagaimana menggunakan FCM.

 - [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging) 


## 🚀 About Me
I'm a full stack developer...

