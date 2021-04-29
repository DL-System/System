
## Installation

#### Docker
```bash
docker run -p 8000:8000 ghcr.io/dl-system/system
```

You can use the application by launching chrome browser and connecting to http://localhost:8000. 

To save your model after docker finishes you can mount a volume to `/system/system/user_data` like so:
```bash
docker run -d \
	--name system \
	--restart unless-stopped \
	-p 8000:8000 \
	-p 55500:55500 \
	-v $(pwd)/data:/system/system/user_data \
	ghcr.io/dl-system/system
```


To login you can use the following credentials:

| Username | Password |
| -------- | ---- |
| test | testtest |
