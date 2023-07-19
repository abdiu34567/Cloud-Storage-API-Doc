# ⚡️ CLOUD STORAGE API ⚡️

Our Cloud Storage API provides a seamless and free solution for users to `upload` and `retrieve` files such as `photos` and `videos`. The API is integrated with Telegram, allowing users to securely store their files on Telegram servers and access them using `unique access keys`.

**Features:**

- **Upload and Retrieve Files:** Users can easily upload their photos and videos to the Cloud Storage API. They can also retrieve their files whenever needed, ensuring easy access to their media content.

- **Telegram Integration:** The API leverages Telegram's robust infrastructure to store and manage user files, ensuring a secure and reliable storage solution.

- **Unique Access Keys:** Each user is provided with a unique access key token that combines their Telegram account ID and a random number. This access key ensures secure and private access to their stored files.

**Supported File Types:**

Currently, the API supports the following file types:

- `Photos (image files)`
- `Videos`

**Future Enhancements:**

We have plans to expand the API's capabilities in the future to include additional file types, such as audio and documents, based on user feedback and needs.

**Terms and Conditions:**

- `Data Retention:` We do not delete your files from the Telegram servers, but please note that the API relies on Telegram's infrastructure, and we cannot guarantee the duration for which your files will be stored on their servers.

- `Recommended Usage:` Our Cloud Storage API is ideal for non-confidential projects where users seek a convenient and free file storage solution. For sensitive or confidential data, we recommend using specialized storage services with dedicated security measures.

**Note:**

As we continue to improve our API, we value user feedback and will consider adding new features and functionalities to meet the evolving needs of our users. We aim to provide a user-friendly and reliable cloud storage solution integrated with Telegram, offering a seamless experience for file management and access.

---

<br>

## Get Access

🌟 First, you need to `register` and get `access_key` token.

> **To Register:**
>
> - **https://t.me/CloudAuthorizeBot**

<br>

> Base Url : https://unlimited-cloud-storage-api.vercel.app/api

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
      .post(
        "https://unlimited-cloud-storage-api.vercel.app/api/upload",
        formData,
        {
          headers: {
            access_key: "Your access key",
            "Content-Type": "multipart/form-data",
          },
        }
      )
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
    .get("https://unlimited-cloud-storage-api.vercel.app/api/getfile/myfile", {
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

**[Get]** ⚡️ https://unlimited-cloud-storage-api.vercel.app/api/getposts

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
      "https://cdn4.telegram-cdn.org/file/CsXCohVeqFeBVQaV2SMdCVbZhZeoa3qVH0wFYUOWsnM17F80y_1NfnZCt2YFwjiGpVPlwstxp1fx4OUg_PnxFrBKydTrs2pZeqZwQ8fFGHz-cfiynyY_hfvbW5k0aqSX5ZKb5sfBKbI7Gj7kSYFTSjWw2xah4T4_xkFw3sf50P56XPK-9CGsAJf28BdVgWTp7uSSQcMCJPtsZ9aRPUyOGzcnV7Fo8_rPszry1sSG0VD5I904DzCmKGc4wDjXOa9OtAcgwFgepaAcEfURtQHVHPII89H8t_n7ggkNXc8NKNF3lbM9jloLyO7h4LyOU_Sj-uvHRhg.mp4",
  },
];
```
