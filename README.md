## demo app - developing with Docker

This demo app shows a simple user profile app set up using 
- index.html with pure js and css styles
- nodejs backend with express module
- mongodb for data storage

All components are docker-based

### With Docker

#### To start the application

Step 1: Create docker network

    docker network create mongo-network 

Step 2: start mongodb 

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: start mongo-express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

_NOTE: creating docker-network in optional. You can start both containers in a default network. In this case, just emit `--net` flag in `docker run` command_

Step 4: open mongo-express from browser

    http://localhost:8081

Step 5: create `user-account` _db_ and `users` _collection_ in mongo-express

Step 6: Start your nodejs application locally - go to `app` directory of project 

    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000

### With Docker Compose

#### To start the application

Step 1: start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
    
_You can access the mongo-express under localhost:8080 from your browser_
    
Step 2: in mongo-express UI - create a new database "my-db"

Step 3: in mongo-express UI - create a new collection "users" in the database "my-db"       
    
Step 4: start node server 

    npm install
    node server.js
    
Step 5: access the nodejs application from browser 

    http://localhost:3000

#### To build a docker image from the application

    docker build -t my-app:1.0 .       
    
The dot "." at the end of the command denotes location of the Dockerfile.
# setup

```
demo
├─ .git
│  ├─ COMMIT_EDITMSG
│  ├─ FETCH_HEAD
│  ├─ HEAD
│  ├─ ORIG_HEAD
│  ├─ config
│  ├─ description
│  ├─ hooks
│  │  ├─ applypatch-msg.sample
│  │  ├─ commit-msg.sample
│  │  ├─ fsmonitor-watchman.sample
│  │  ├─ post-update.sample
│  │  ├─ pre-applypatch.sample
│  │  ├─ pre-commit.sample
│  │  ├─ pre-merge-commit.sample
│  │  ├─ pre-push.sample
│  │  ├─ pre-rebase.sample
│  │  ├─ pre-receive.sample
│  │  ├─ prepare-commit-msg.sample
│  │  ├─ push-to-checkout.sample
│  │  └─ update.sample
│  ├─ index
│  ├─ info
│  │  └─ exclude
│  ├─ logs
│  │  ├─ HEAD
│  │  └─ refs
│  │     ├─ heads
│  │     │  └─ main
│  │     └─ remotes
│  │        └─ origin
│  │           └─ main
│  ├─ objects
│  │  ├─ 03
│  │  │  └─ 91c47836b90d2d69b3a76525a5737cfa403a3e
│  │  ├─ 05
│  │  │  └─ 6263ccda403a16526d20f5b575cfbcacd1b305
│  │  ├─ 09
│  │  │  └─ 15d15eb935dfb1be048a15b82925508b963c18
│  │  ├─ 10
│  │  │  └─ 9770deb9fb23e79d06e761efa55f04a97d1e80
│  │  ├─ 14
│  │  │  └─ 4f8ce61b0bee4517361431832b14fa2cc37fe0
│  │  ├─ 16
│  │  │  └─ 0a6953f12ef2d36d1e4af98e0dafd024a1a26a
│  │  ├─ 1b
│  │  │  └─ 3cee59495a072999beacaf77792d90d0d698e3
│  │  ├─ 29
│  │  │  └─ 8aec08389c5c797bf14a64fc03cbd26407fb36
│  │  ├─ 2a
│  │  │  └─ bd2104ddd129358e8cb3ab66b68f16adb756f9
│  │  ├─ 3c
│  │  │  └─ 11fef14db949d887c5954c0a0f38e2c88242bd
│  │  ├─ 44
│  │  │  └─ c3dd04383aa92ae779247db9f6e4910a053290
│  │  ├─ 48
│  │  │  └─ d6b185d95e3a32b3e29a3be6807c787ed196fc
│  │  ├─ 4c
│  │  │  └─ 0dcfe997b6854c7e6fac635efb1ba303e44763
│  │  ├─ 5a
│  │  │  └─ 1796df5d1959405853e52f53a6f9863fa33242
│  │  ├─ 62
│  │  │  └─ e81469fe72231ca5b65cf0914655b387cd2779
│  │  ├─ 72
│  │  │  ├─ 078157746f414e5863de375e3a89fa6fbc112d
│  │  │  └─ 5807a94508f19cf5fffcbb17fb19498f2d7c0a
│  │  ├─ 76
│  │  │  └─ 953b51c3b12101502f88c78445be71849af3e0
│  │  ├─ 8a
│  │  │  └─ e03c540f26d3f76b13a1f50679265f5b7e5f92
│  │  ├─ 8b
│  │  │  └─ c65282256dd1dd6c0faee25b2fc2b03a45d499
│  │  ├─ 8d
│  │  │  └─ e019618d202949a0320ef8431ea1493885f011
│  │  ├─ b1
│  │  │  ├─ 1fe652e637596618a70f4d91424fbc24b9a99b
│  │  │  └─ 409c2f12ab4175f51c227f6511769affd1ffbc
│  │  ├─ c2
│  │  │  └─ cb3fd044aadf1e602396bf225002709a208707
│  │  ├─ c3
│  │  │  └─ 0890b7ac38f8c0079016acbcde2b45ec1d2902
│  │  ├─ c4
│  │  │  └─ 37afd1ececb84f83891246329b07ad3266c54e
│  │  ├─ ca
│  │  │  └─ df39a71dd2891009d0d5d8f99961c3be221b87
│  │  ├─ cc
│  │  │  └─ b08c5ce75d10ef4efd0c7fc7d55531715d013b
│  │  ├─ ce
│  │  │  └─ 2411d53498353402600b0d7638375378f4cbef
│  │  ├─ d8
│  │  │  └─ 10bcec2d556e51c1257a0e4fd79011d41fc0be
│  │  ├─ dc
│  │  │  └─ 22b9476a62aeb7c62cd5a7b12b38c93755174e
│  │  ├─ e6
│  │  │  ├─ 8c503f86e07980fd3d873cd007b773cb391988
│  │  │  └─ 9de29bb2d1d6434b8b29ae775ad8c2e48c5391
│  │  ├─ ec
│  │  │  └─ e1cb8a2e77b836db178f91f9e8585e78a4736e
│  │  ├─ f3
│  │  │  └─ 389b09410c5fce69e35e616d45ba8ed602c05c
│  │  ├─ info
│  │  └─ pack
│  └─ refs
│     ├─ heads
│     │  └─ main
│     ├─ remotes
│     │  └─ origin
│     │     └─ main
│     └─ tags
├─ .github
│  └─ workflows
│     └─ main.yml
├─ .gitignore
├─ README.md
├─ app
│  ├─ Dockerfile
│  ├─ images
│  │  ├─ profile-1.jpg
│  │  └─ profile-2.jpg
│  ├─ index.html
│  ├─ package-lock.json
│  ├─ package.json
│  └─ server.js
├─ docker-compose.yml
└─ gitignore

```