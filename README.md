# The Cat API documentation
> The Cat API is a public API of image cat management.

> This is a documentation exercise made for the course workshop **Decolando em TW**.

## 🐱 Upload a specific image

`POST https://api.thecatapi.com/v1/images/upload`

Create a new image on the system by loading a valid file containing a cat.

### **Request**
- You need an **API Key**. If you don't have one, **signup** on [main site](https://thecatapi.com/signup) and get one emailed to you for free.

#### Headers
| Name | Description | Mandatory | Example
|--|--|--|--|
| `x-api-key` | Token generated when make a sign up. | Yes | `{ "x-api-key" : "live_UIHAbdibiudbI" }`
  
#### Body
> **Payload type:** form-data.

| Name | Description | Type | Mandatory
|--|--|--|--|
| `file` | File in .gif, .png, or .jpg | `file` | Yes
| `sub_id` | ID for internal identification. | `string` | No

### **Responses**

-  `201 Created`
> **Response type:** application/json
```json
{
  "id": "6WZJ7r8LS",
  "url": "https://cdn2.thecatapi.com/images/6WZJ7r8LS.png",
  "width": 628,
  "height": 600,
  "original_filename": "cat1.png",
  "pending": 0,
  "approved": 1
}
```

-  `400 Bad request`
> **Response type:** application/text

```
Classifcation failed: correct animal not found.
```
- `401 Unauthorized`
> **Response type:** application/text

```
AUTHENTICATION_ERROR - you need to send your API Key as the 'x-api-key' header
```
- `500 Internal Sever Error`
> **Response type:** application/text

```
Internal Server Error
```
## 🐱 Get image

`GET https://api.thecatapi.com/v1/images/{{image_id}}`

Get a specific image.

### **Request**
- You need an **API Key**. If you don't have one, **signup** on [main site](https://thecatapi.com/signup) and get one emailed to you for free.

#### Headers
| Name | Description | Mandatory | Example
|--|--|--|--|
| `x-api-key` | Token generated when make a sign up. | Yes | `{ "x-api-key" : "live_UIHAbdibiudbI" }`

#### Path Parameters
| Name | Description | Example
|--|--|--|
| `image_id` | The image ID. | `6WZJ7r8LS` |

### **Responses**

-  `200 OK`
> **Response type:** application/json
```json
{
  "id":  "6WZJ7r8LS",
  "url":  "https://cdn2.thecatapi.com/images/6WZJ7r8LS.png",
  "width":  628,
  "height":  600,
  "sub_id":  null
}
```
-  `400 Bad request`
> **Response type:** application/text

```
Couldn't find an image matching the passed 'id' of 6WZJ7r8LSa
```
- `401 Unauthorized`
> **Response type:** application/text
```
AUTHENTICATION_ERROR - you need to send your API Key as the 'x-api-key' header
```

## 🐱 Get your uploaded images

`GET https://api.thecatapi.com/v1/images`

Get all your uploaded images.

### **Request**
- You need an **API Key**. If you don't have one, **signup** on [main site](https://thecatapi.com/signup) and get one emailed to you for free.

#### Headers
| Name | Description | Mandatory | Example
|--|--|--|--|
| `x-api-key` | Token generated when make a sign up. | Yes | `{ "x-api-key" : "live_UIHAbdibiudbI" }`

#### Query Parameters
| Name | Description | Type | Mandatory | Example
|--|--|--|--|--|
| `limit` | The images quantity that will be returned. The default value is 1 and the maximum is 25. | `integer`| No | `1`
| `mime_types` | Filter images by types: .gif, .jpg or .png. You can pass multiple types separated by commas. By default it will returns all images. | `string`| No | `.gif,.jpg`
| `order` | You can order the return by the date time creation: RANDOM, ASC or DESC. The default is RANDOM. | `string`| No | `ASC`

### **Responses**

-  `200 OK`
> **Response type:** application/json
```json
[
  {
    "breeds":  [],
    "id":  "6WZJ7r8LS",
    "url":  "https://cdn2.thecatapi.com/images/6WZJ7r8LS.png",
    "width":  628,
    "height":  600,
    "sub_id":  null,
    "created_at":  "2022-12-01T22:26:20.000Z",
    "original_filename":  "cat1.png",
    "breed_ids":  null
  }
]
```

- `401 Unauthorized`
> **Response type:** application/text
```
AUTHENTICATION_ERROR - you need to send your API Key as the 'x-api-key' header
```

## 🐱 Delete a specific image

`DELETE https://api.thecatapi.com/v1/images/{image_id}`

Delete a specific image.

### **Request**
- You need an **API Key**. If you don't have one, **signup** on [main site](https://thecatapi.com/signup) and get one emailed to you for free.

#### Headers
| Name | Description | Mandatory | Example
|--|--|--|--|
| `x-api-key` | Token generated when make a sign up. | Yes | `{ "x-api-key" : "live_UIHAbdibiudbI" }`

#### Path Parameters
| Name | Description | Example
|--|--|--|
| `image_id` | The image ID. | `6WZJ7r8LS` |

### **Responses**

-  `204 No Content`
The image has been deleted with success.

-  `400 Bad request`
> **Response type:** application/text

```
INVALID_DATA
```
- `401 Unauthorized`
> **Response type:** application/text
```
AUTHENTICATION_ERROR - you need to send your API Key as the 'x-api-key' header
```