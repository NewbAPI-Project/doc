---
sidebar_position: 3
---

# QR Code

<!-- # QRcode Generator Documentation -->
API version: `2.0`

## Introduction
Looking for a quick and easy way to integrate QR code functionality into your application? Look no further than our QR code API! With just a few simple API calls, you can generate and display QR codes with ease, allowing your users to quickly and easily scan and interact with your content. Our API is fast, reliable, and easy to use, making it the perfect choice for developers looking to add QR code functionality to their applications. So why wait? Try our QR code API today and take your application to the next level!

<img src="../img/rapidapi.svg" width="150" />

Link: [Rapid](https://rapidapi.com/newbAPIOfficial/api/qr-code-by-newbapi)

#### Supported output file:
- `.png`
- `.pdf`
- `.eps`

## API Endpoint

| Endpoint            	   | Method  | Description |
| ------------------------ | --------| ------------|
| `/api/v2/qr`  					 | `POST`  | Generate standard QR code|
| `/api/v2/wifi`						 | `POST` | Generate WiFi QR code |
| `/api/v2/sms`						 | `POST` | Generate SMS QR code |
| `/api/v2/tel`						 | `POST` | Generate Telephone Number QR code |
| `/api/v2/email`						 | `POST` | Generate Email QR code |
| `/api/v2/event`						 | `POST` | Generate Calendar event QR code |
| `/api/v2/vccard`						 | `POST` | Generate VC Card QR code |
| `/api/v2/geo`						 | `POST` | Generate Geo QR code |

## Schemas

### `data`

##### Standard QR
	
Suitable for URL and Text

- `data` (required) - String

```json
"data": "Hello World"
```

##### Full Example `Standard`

```json
{
    "data": "https://newbapi.com",
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "myqrcode"
    }
}
```

##### Wifi QR

- `type` (required) - String. Example: `WEP`, `WPA`,  `WPA2`, `WPA3`
- `ssid` (required) - String. Example: `My home wifi`
- `password` (optional) - String

```json
"data": {
	"type": "WPA",
	"ssid": "My Home Wifi",
	"password": "password_wifi"
}
```

##### Full Example `Wifi`

```json
{
    "data": {
        "type": "WPA",
        "ssid": "mywifiname",
        "password": "12345667"
    },
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "mywifi"
    }
}
```

##### SMS QR

- `sms` (required) - String
- `body` (required) - String

```json
"data": {
	"sms": "092012312",
	"body": "Hello This is me"
}
```

##### Full Example `SMS`

```json
{
    "data": {
        "sms": "8291283912",
        "body": "mymessage"
    },
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "smsqr"
    }
}
```

##### Tel QR

- `tel` (required) - String

```json
"data": {
	"tel": "0292012312"
}
```

##### Full Example `Tel`

```json
{
    "data": {
        "tel": "92839238129"
    },
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "mytel"
    }
}
```

##### Email

- `mailto` (required) - String
- `subject` (required) - String
- `body` (required) - String
- `cc` (optional) - String
- `bcc` (optional) - String

```json
"data": {
	"mailto": "jaironlanda@example.com",
	"cc": "someone@example.com",
	"bcc": "huhu@example.com",
	"subject": "This subject",
	"body": "my body"
}
```

##### Full Example `Email`

```json
{
    "data": {
        "mailto": "jaironlanda@example.com",
        "subject": "This is QRcode email",
        "cc": "someone@example.com",
        "bcc": "huhu@example.com",
        "body": "Hi newbapi.com!"
    },
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "myemail"
    }
}
```

##### Calendar Event

:::info

- Timezone: `UTC`
- Date and Time Format: `Y-m-d H:M:S`

:::

- `summary` (required) - String
- `date_start` (optional) - String.
- `date_end` (optional) - String.
- `location` (optional) - String
- `description` (optional) - String

```json
"data": {
	"summary": "My Life event",
	"date_start": "2024-04-13 12:12:00",
	"date_end": "2024-04-14 12:12:00",
	"location": "Singapore",
	"description": "QR code Party"
}
```

##### Full Example `Calendar Event`

```json
{
    "data": {
        "summary": "My Qr Code Party!",
        "date_start": "2023-04-04 12:30:00",
        "date_end": "2023-04-05 12:30:00",
        "location": "Singapore",
        "description": "QR code Party"
    },
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "myevent"
    }
}
```

##### VC Card

- `firstname` (required) - String
- `lastname` (optional) - String
- `tel` (optional) - String
- `email` (optional) - String

```json
"data": {
	"firstname": "Jairon",
	"lastname": "Landa",
	"tel": "9201293121",
	"email": "jaironlanda@example.com"
}
```

##### Full Example `VC Card`

```json
{
    "data": {
        "firstname": "Jairon",
        "lastname": "Landa",
        "tel": "89212312",
        "email": "jaironlanda@example.com"
    },
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "myvccard"
    }
}
```

##### Geo

- `lat` (required) - String
- `long` (required) - String

```json
"data": {
	"lat": "19.80604815524197",
	"long": "-155.53058872342245"
}
```

##### Full Example `Geo`

```json
{
    "data": {
        "lat": "19.80604815524197",
        "long": "-155.53058872342245"
    },
    "config": {
        "auto": true,
        "version": 1,
        "error_correction": "M",
        "box_size": 30,
        "border": 4
    },
    "design": {
        "qr_colour": "#000000",
        "bg_colour": "#ffffff"
    },
    "option": {
        "file_type": "png",
        "file_name": "mygeo"
    }
}
```

### `config`

QR Code configuration

- `auto` (required) - Boolean: `true` or `false`. Default: `true`
- `version` (required) - Integer: `1` to `40`
- `error_correction` (required) String: `L`, `M`, `Q`, and `H`. Default: `M`
- `box_size` (required) - Integer - How many Pixels each "box" of the QR code is.
- `border` (required) - Integer - How many boxes thick the border should be. Default: `4` 

```json
"config": {
	"auto": true,
	"version": 1,
	"error_correction": "M",
	"box_size": 30,
	"border": 4
}
```

### `design`

Colour code is hex color. Example `#000000`

- `qr_colour` (required) - String
- `bg_colour` (required) - String


```json
"design": {
    "qr_colour": "#000000",
    "bg_colour": "#ffffff"
  }
```

### `option`

- `file_type` (required) - String. Supported file type: `png`, `pdf`, and `eps`
- `file_name` (required) - String.

```json
  "option": {
    "file_type": "png",
    "file_name": "myevent"
  }
```

## Response

The response will be returned as binary.

```bash
{
  "access-control-allow-credentials": "true",
  "access-control-allow-origin": "*",
	...
  "content-disposition": "attachment; filename=\"myqrcode.png\"",
  "content-length": "5870",
  "content-type": "image/png",
	...
  "server": "RapidAPI-1.2.8",
  "strict-transport-security": "max-age=63072000",
  "x-rapidapi-region": "AWS - ap-southeast-1",
  "x-rapidapi-version": "1.2.8"
}
```

## Example (JavaScript - Fetch)

```javascript
const data = {
  data: "https://newbapi.com",
  config: {
    auto: true,
    version: 1,
    error_correction: "M",
    box_size: 30,
    border: 4
  },
  design: {
    qr_colour: "#000000",
    bg_colour: "#ffffff"
  },
  option: {
    file_type: "png",
    file_name: "myqrcode"
  }
};

fetch(url, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(data)
})
.then(response => {
  const fileName = response.headers.get('content-disposition').split('filename=')[1];
  return response.blob().then(blob => {
    const url = window.URL.createObjectURL(new Blob([blob]));
    const link = document.createElement('a');
    link.href = url;
    link.setAttribute('download', fileName);
    document.body.appendChild(link);
    link.click();
    link.parentNode.removeChild(link);
  });
})
.catch(error => {
  // handle network errors
});
```