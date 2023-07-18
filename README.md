# ⚡️ CLOUD STORAGE API ⚡️

> Base Url : https://localhost:3000/api

<br>

## End-Points:

- ⚡️`upload/`
- ⚡️`getfile/{file_name}`
- ⚡️`getposts/`

<br>

## upload:

<br>

### Example:

```js
const axios = require("axios");
const FormData = require("form-data");
const fs = require("fs");

const uploadFile = async () => {
  try {
    const formData = new FormData();

    //add file loaction in array
    const files = ["friend.jpg", "new.jpg"];

    files.forEach((filePath) => {
      const fileStream = fs.createReadStream(filePath);

      //the field name to include the file must be "file"
      formData.append("file", fileStream);
    });

    await axios
      .post("http://localhost:3000/api/upload", formData, {
        headers: {
          access_key: "Your access key",
          "Content-Type": "multipart/form-data",
        },
      })
      .then(function (response) {
        console.log(response.data.message);
      })
      .catch((err) => {
        console.log(err.response.data);
      });
  } catch (error) {
    console.error(error);
  }
};

uploadFile();
```

<br>

### Response Body:

```js
{
  message: "Files uploaded successfully";
}
```

<br>

## getfile/{name}

<br>

### Example:

**[Get]** ⚡️ https://localhost:3000/api/getfile/myfile

<br>

```js
const axios = require("axios");

const getFile = async () => {
  await axios
    .get("http://localhost:3000/api/getfile/myfile", {
      headers: {
        access_key: "Your access key",
      },
    })
    .then(function (response) {
      console.log(response.data.message);
    })
    .catch((err) => {
      console.log(err.response.data);
    });
};

getFile();
```

<br>

### Response Body:

```js
[
  {
    id: 72,
    title: "myfile_a.jpg",
    photo:
      "https://cdn4.telegram-cdn.org/file/CsXCohVeqFeBVQaV2SMdCVbZhZeoa3qVH0wFYUOWsnM17F80y_1NfnZCt2YFwjiGpVPlwstxp1fx4OUg_PnxFL0GykOf1vXY_yfhrBKydTrs2pZeqZwQ8fFGHz-cfiynyY_hfvbW5k0aqSX5ZKb5sfBKbI7Gj7kSYFTSjWw2xah4T4_xkFw3sf50P56XPK-9CGsAJf28BdVgWTp7uSSQcMCJPtsZ9aRPUyOGzcnV7Fo8_rPszry1sSG0VD5I904DzCmKGc4wDjXOa9OtAcgwFgepaAcEfURtQHVHPII89H8t_n7ggkNXc8NKNF3lbM9jloLyO7h4LyOU_Sj-uvHRhg.jpg",
  },
];
```

## getposts

<br>

### Example:

**[Get]** ⚡️ https://localhost:3000/api/getposts

<br>

```js
const axios = require("axios");

const getPosts = async () => {
  await axios
    .get("http://localhost:3000/api/getposts", {
      headers: {
        access_key: "Your access key",
      },
    })
    .then(function (response) {
      console.log(response.data.message);
    })
    .catch((err) => {
      console.log(err.response.data);
    });
};

getPosts();
```

### Response Body:

<br>

```js
[
  {
    id: 72,
    title: "love.jpg",
    photo:
      "https://cdn4.telegram-cdn.org/file/CsXCohVeqFeBVQaV2SMdCVbZhZeoa3qVH0wFYUOWsnM17F80y_1NfnZCt2YFwjiGpVPlwstxp1fx4OUg_PnxFL0GykOf1vXY_yfhrBKydTrs2pZeqZwQ8fFGHz-cfiynyY_hfvbW5k0aqSX5ZKb5sfBKbI7Gj7kSYFTSjWw2xah4T4_xkFw3sf50P56XPK-9CGsAJf28BdVgWTp7uSSQcMCJPtsZ9aRPUyOGzcnV7Fo8_rPszry1sSG0VD5I904DzCmKGc4wDjXOa9OtAcgwFgepaAcEfURtQHVHPII89H8t_n7ggkNXc8NKNF3lbM9jloLyO7h4LyOU_Sj-uvHRhg.jpg",
  },
  {
    id: 73,
    title: "vid.mp4",
    video:
      "https://cdn4.telegram-cdn.org/file/CsXCohVeqFeBVQaV2SMdCVbZhZeoa3qVH0wFYUOWsnM17F80y_1NfnZCt2YFwjiGpVPlwstxp1fx4OUg_PnxFrBKydTrs2pZeqZwQ8fFGHz-cfiynyY_hfvbW5k0aqSX5ZKb5sfBKbI7Gj7kSYFTSjWw2xah4T4_xkFw3sf50P56XPK-9CGsAJf28BdVgWTp7uSSQcMCJPtsZ9aRPUyOGzcnV7Fo8_rPszry1sSG0VD5I904DzCmKGc4wDjXOa9OtAcgwFgepaAcEfURtQHVHPII89H8t_n7ggkNXc8NKNF3lbM9jloLyO7h4LyOU_Sj-uvHRhg.jpg",
  },
];
```
