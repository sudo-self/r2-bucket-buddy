# Bucket Buddy

```
npm create cloudflare@latest -- your-worker-name
```

R2 storage objects primary functions.

1. GET
2. PUT
3. DELETE
4. LIST

Replace src `index.js `with the one in this repo. 

## R2 binding

 Wrangler.toml
```
[[r2_buckets]]
binding = 'MY_BUCKET'
bucket_name = 'your-bucket-name-here'
```

## R2 CORS policy

**Need it from worker --> bucket on the same origin**

```
[
  {
    "AllowedOrigins": [
      "http://YOUR-BUCKET-NAME",
      "https://YOUR-WORKER-NAME"
    ],
    "AllowedMethods": [
      "GET",
      "PUT",
      "POST",
      "DELETE"
    ],
    "AllowedHeaders": [
      "*"
    ],
    "ExposeHeaders": [
      "Content-Length",
      "Content-Type"
    ],
    "MaxAgeSeconds": 3600
  }
]
```
place an R2 storage API token from cloudflare

```
wrangler secret put MY_BUCKET
```
Then the API KEY as the secret ***************<br>

Deploy your worker

```
npx wrangler deploy
```

Visit the your worker URL and it should say "object not found" 404

```
<YOUR_WORKER>.<YOUR_SUBDOMAIN>.workers.dev
```

R2&nbsp;<a href="https://developers.cloudflare.com/r2/api/workers/workers-api-usage/">workers api docs</a><br>

configure your bucket for public acess then upload the `index.html` from this repo

<YOUR_WORKER>.<YOUR_SUBDOMAIN>.workers.dev/<strong>index.html</strong><br>

Now have a mini GUI to interact with your R2<br>

1.GET
2.PUT
3.DELETE
4.LIST

<img width="832" alt="Screenshot 2024-09-11 at 10 21 01 PM" src="https://github.com/user-attachments/assets/9be1a2e6-0623-4259-b759-942b12e43e9a">






