## Deploy Node.js Backend API to Kubernetes

1. Create basic express app

```js
const express = require('express')

const app = express()

app.get('/', (req,res) => {
  res.send('API Running')
})

const port = 3000

app.listen(port, () => console.log(`listening on port: ${port}`))
```

2. Create Local Docker Image

```js
FROM node:13-alpine

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install --production

COPY . .

EXPOSE 3000

CMD node index.js
```



[Quickstart - Store Docker container images in Artifact Registry](https://cloud.google.com/artifact-registry/docs/docker/store-docker-container-images)

3. Push docker image to Artifact Registry


[Quickstart - Deploy an app to a GKE cluster](https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster#dockerfile)

4. Create a GKE cluster
- Get authentication credentials for the cluster


5. Deploy an application to the cluster
- Create the Deployment
- Expose the Deployment
