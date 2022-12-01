# The Cat API documentation

## Upload a specific image

`POST https://api.thecatapi.com/v1/images/upload`

### Request

#### Headers

#### Body

### Responses

- `201 Created`


``` json
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

- `400 Bad request`