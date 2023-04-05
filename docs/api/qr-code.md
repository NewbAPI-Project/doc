---
sidebar_position: 3
---

# QR Code

<!-- # QRcode Generator Documentation -->
API version: `2.0`

## Introduction
Looking for a quick and easy way to integrate QR code functionality into your application? Look no further than our QR code API! With just a few simple API calls, you can generate and display QR codes with ease, allowing your users to quickly and easily scan and interact with your content. Our API is fast, reliable, and easy to use, making it the perfect choice for developers looking to add QR code functionality to their applications. So why wait? Try our QR code API today and take your application to the next level!

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

## API Schemas

### `data`

##### Standard QR
	
Suitable for URL and Text

- `data` (required) - String

```json
"data": "Hello World"
```

##### Wifi QR

- `type` (required) - String. Example: `WEP`, `WPA`,  `WPA2`, `WPA3`
- `ssid` (required) - String. Example: `My home wifi`
- `password` (optional) - String

```json
"data": {
	"type": "WPA", // WEP
	"ssid": "My Home Wifi",
	"password": "password_wifi"
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

##### Tel QR

- `tel` (required) - String

```json
"data": {
	"tel": "0292012312"
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

##### Calendar Event

:::info

Timezone: `UTC`. Date and Time Format: `Y-m-d H:M:S`

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
	"location": "Rmh saya",
	"description": "my haus"
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

##### Geo

- `lat` (required) - String
- `long` (required) - String

```json
"data": {
	"lat": "19.80604815524197",
	"long": "-155.53058872342245"
}
```

### `config`

QR Code configuration

- `auto` (required) - Automatic detect Boolean: `true` or `false`

```json
"config": {
	"auto": true,
	"version": 1,
	"error_correction": "M",
	"box_size": 30,
	"border": 4
}
```

```bash

{
  "data": {
    "summary": "My Life event",
    "date_start": "2024-04-13 12:12:00",
    "date_end": "2024-04-14 12:12:00",
    "location": "Rmh saya",
    "description": "my haus"
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

## Exampe API Response

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


## API request body


| Parameter / Query | Type         | Default | Description      | Example
| ----------------- | ------------ | --------| ---------------- | ---------------------------
| data              | `string`     | `none`  | Qr code data     | `https:\\jaironlanda.com` or `this is normal text`


### Request body `config`

| Parameter / Query | Type         | Default | Description      | Example
| ----------------- | ------------ | --------| ---------------- | ----------
| auto              | `boolean`     | `true`  | Generate qr code with default config. Default Config: `"version": 1`, `"error_correction": "M"`, `"box_size": 10`, `"border": 4` | -
| version    | `integer`    | `1` | Supported qr code version: `1` until `40` | -
| error_correction  | `string`     | `'M'`   | Error correction config: `L`, `M` (default), `Q`, and `H` | -
| box_size| `integer`      | `10`  | Minimum: `10`, Maximum: `100` | -
| border  | `integer`      | `4`  | Minimum: `4`| -

#### Example #1:

Generate qr code with config `"auto": true`. Parameter `version`, `error_correction`, `box_size`, and `border` is not require.
```
{
    "data": "jaironlanda.com",
    "config": {
        "auto": true
    },
    "option": {
        "file_type": "png"
    }
}
```
> Note: `design` parameter is optional. Default color is black and white.

#### Example #2:
To generate qr code with custom config set `auto` parameter to `false`.

```
{
    "data": "jaironlanda.com",
    "config": {
        "auto": false,
        "version": 20,
        "error_correction": "L",
        "box_size": 50,
        "border": 10
    },
    "option": {
        "file_type": "png"
    }
}
```
> Note: `design` parameter is optional. Default color is black and white.

### Request body `design`

> Note: Support color format `Hex color` only. More info [here](https://www.color-hex.com/)

| Parameter / Query | Type         | Default | Description      | Example
| ----------------- | ------------ | --------| ---------------- | ----------
| qr_colour         | `string`     | `#000000`  | Qr code color, default is black color or `#000000` | -
| bg_colour    		| `string`    | `#ffffff` | Background for qr code, default is white color or `#ffffff` | -

#### Example #3:
Generate qr code with custom color and auto config.
```
{
    "data": "jaironlanda.com",
    "config": {
        "auto": true
    },
    "design": {
        "qr_colour": "#f69273",
        "bg_colour": "#cc0000"
    },
    "option": {
        "file_type": "png"
    }
}
```
#### Example #4:
Generate qr code with custom color and manual config.
```
{
    "data": "jaironlanda.com",
    "config": {
       "auto": false,
        "version": 20,
        "error_correction": "L",
        "box_size": 50,
        "border": 10
    },
    "design": {
        "qr_colour": "#f69273",
        "bg_colour": "#cc0000"
    },
    "option": {
        "file_type": "png"
    }
}
```

### Request body `option`

| Parameter / Query | Type         | Default | Description      | Example
| ----------------- | ------------ | --------| ---------------- | ----------
| file_type              | `string`     | `png`  | support file type: `png`, `pdf`, `eps`, and `svg`| -
| file_name    | `string`    | `none` | if value is none, file name will randomly generate | -

#### Example #5:
Generate qr code with `pdf` format. Supported file type: `png`, `pdf`, `eps`, and `svg`
```
{
    "data": "jaironlanda.com",
    "config": {
        "auto": true
    },
    "option": {
        "file_type": "pdf"
    }
}
```

#### Example #5:
Generate qr code with `pdf` file type and manual config setup.
```
{
    "data": "jaironlanda.com",
    "config": {
        "auto": false,
		"version": 20,
        "error_correction": "L",
        "box_size": 50,
        "border": 10
    },
    "design": {
        "qr_colour": "#f69273",
        "bg_colour": "#cc0000"
    },
    "option": {
        "file_type": "pdf",
		"file_name": "this is my qrcode"
    }
}
```

### Schema

Schema for API request: 
```
{
	"title": "QrText",
	"required": [
		"config",
		"option"
	],
	"type": "object",
	"properties": {
		"data": {
			"title": "Data",
			"type": "string",
			"default": "jaironlanda.com"
		},
		"config": {
			"title": "QrConfig",
			"type": "object",
			"properties": {
				"auto": {
					"title": "Auto",
					"type": "boolean",
					"default": true
				},
				"version": {
					"title": "Version",
					"type": "integer",
					"default": 1
				},
				"error_correction": {
					"title": "Error Correction",
					"type": "string",
					"default": "M"
				},
				"box_size": {
					"title": "QR code Box Size minium is 10",
					"maximum": 100,
					"minimum": 10,
					"type": "integer",
					"default": 30
				},
				"border": {
					"title": "Border",
					"type": "integer",
					"default": 4
				}
			}
		},
		"design": {
			"title": "QrDesign",
			"type": "object",
			"properties": {
				"qr_colour": {
					"title": "Qr Colour",
					"type": "string",
					"default": "#000000"
				},
				"bg_colour": {
					"title": "Bg Colour",
					"type": "string",
					"default": "#ffffff"
				}
			}
		},
		"option": {
			"title": "QrOption",
			"type": "object",
			"properties": {
				"file_type": {
					"title": "File Type",
					"type": "string",
					"default": "png"
				},
				"file_name": {
					"title": "File Name",
					"type": "string"
				}
			}
		}
	}
}
```
## API response

```
....
"content-disposition":"attachment; filename*=utf-8''<file-name-here>.<file-format>"
"content-type":"<content type>"
....
```

List of `content-type`:
- PDF: `application/pdf`
- EPS: `application/postscript`
- PNG:  `image/png`
- SVG: `image/svg+xml`