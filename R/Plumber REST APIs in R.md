



# Building REST APIs with R and Plumber

REST stands for “Representational State Transfer”, meaning it represents a set of rules developers follow when creating APIs (i.e. you get a responding piece of data, the response, whenever you make a request to a particular URL).

Every request is composed of these four parts:

1. **Endpoint** - a part of the URL - The endpoint for `https://example.com/predict` is `/predict`.
2. **Method** - a type of request you’re sending; used to perform one of these actions: *Create, Read, Update, Delete (CRUD)*. Can be one of the following:
   - `GET`
   - `POST`
   - `PUT`
   - `PATCH`
   - `DELETE`
3. **Headers** – used for providing information (think authentication credentials, for example). They are provided as key-value pairs.
4. **Body** – information that is sent to the server. Used only when not making `GET` requests.

Most of the time, the response returned after making a request is in JSON format. The alternative format is XML, but JSON is more common. You can also return other objects, such as images instead. You’ll learn how to do that today.

R allows you to develop REST APIs with the plumber package. You can read the official documentation here.

It’s easy to repurpose any R script file to an API with plumber, because you only have to decorate your functions with comments. You’ll see all about it in a bit.



