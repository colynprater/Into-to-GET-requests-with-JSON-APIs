# Into to GET requests with JSON APIs

An API is an INTERFACE (the last letter of the abbreviation, forget the first two), which in this context we use to send REQUESTS to and receive a JSON RESPONSE.

## JSON

JSON stands for `JavaScript Object Notation`. But all we care about is the 'O' for `Object`. Everything starting with `{` and and ending in a `}` is an Object, and inside them are `keys` and `values`.

### Example

```
{"name": "Tupac"}
```

`'name':` was the key and `'Tupac'` was the value. The `value` can be anything: a string, an integer, a list or even another Object.
To dive in the deep end, here's an example of a typical Moneysmart API JSON response. After we've sent a GET REQUEST, this is what we'll receive when successful.

```
{
  "data": [
        {
            "id": 777,
            "type": "product",
            "attributes": {
                "name": "Harambe",
                "slug": "harambe-slug"
            }
        },
        {
            "id": 888,
            "type": "product",
            "attributes": {
                "name": "Cecil",
                "slug": "cecil-slug"
            }
        }
    ]    
}
```

So we get one parent Object back, it has one key: `'data'`, whose value is a list (starts with `[` and ends with `]`). The list has two Objects inside. Those two objects in the list are of course Moneysmart products, this is our data. Notice all the `Objects` (starting with `{` and and ending in a `}`) have their keys and values. The `'attributes'` key has an entire `Object` as its value. Now you're an expert on reading and understanding JSON. If not, read on anyway and it will make sense soon.

## GET REQUESTS

There are several methods of REQUESTS other than GET, but here we're only covering GET. There are countless ways to go about making a REQUEST. If you're a programmer you can write a script, but that isn't necessary, in fact for a GET you can just open your browser, enter the desired API endpoints URL and the browser will make the GET request for you. Smart individuals will go a step further and download something like [POSTMAN](https://www.getpostman.com/apps), allowing them to make any kind if request without writing code.


## Making a GET REQUEST

Moneysmart API envoronments come and go, so for now we'll use a practicve API that returns album names in a JSON reponse.
Place the following url in your browser or POSTMAN app to send a GET REQUEST and receive a JSON response.
`https://jsonplaceholder.typicode.com/users/1/albums`
If all goes well the response should look something like.

```
[
    {
        "userId": 1,
        "id": 1,
        "title": "All Eyez On Me"
    },
    {
        "userId": 1,
        "id": 2,
        "title": "Loyal to the Game"
    }
]
```

## Using the API interface (params 101)

That request was one thing, but now we'll use the `I` in API. We interact with the interface using `params`. Different interfaces accept different params, so if you don't send them correctly, it's likely you wont get the response you're looking for. API's with good documentation will tell you exactly which params to use for which purpose.
Params also work on a key-value system, like the Objects we learned about earlier. This practice API accepts the params: `title`, and `id`.
To use params, we append them to the end of the url we use to make the REQUEST, that's it. There is a specific syntax to it though.
To give a value for `title` param, the syntax would be `?title=all eyez on me`.
The `?` declares the beginning of the `key`, and the `=` declares the beginning of the `value`.

### Example

```
https://jsonplaceholder.typicode.com/users/1/albums?title=quidem molestiae enim
```
The endpoint url was `https://jsonplaceholder.typicode.com/users/1/albums`, and we just added the params with `?title=quidem molestiae enim`

#### Using multiple params
You can use as many different params as you like, with the following syntax:
`?title=all eyez on me&id=1`
Here we're specifying the value for `title` ('all eyez on me'), and also for `id` (1).

Look closely and you'll notice the first param (`title`) was declared with a `?` but the second param (`id`) was declared with a `&`.
By convention, the first param key is declared with `?` and any subsequent ones are declared with `&`, thats [just the way it is](https://youtu.be/Ay9BWM8lwOA?t=86).

### Example
```
https://jsonplaceholder.typicode.com/users/1/albums?title=quidem molestiae enim&id=1
```

## Exercises

Make the GET REQUESTS shown in the examples above.

- make requests without params.
- make requests with params.
- make requests with params you just made up eg: `?fruit=banana`, see if you can break the API or get it to return nothing.

## Moving forward
Now that you've mastered GET REQUESTS, use a real [Moneysmart API](https://github.com/moneysmartco/sg_personal_loan/wiki/Sg-Personal-Loan--Products-API) and make use of its features (sorting, filtering, selecting particular fields). The environment (and therefore urls) are often changing you so may need to reach out to DevOps to get started.
