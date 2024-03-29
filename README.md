# System

## Installation

### Minimal

```bash
docker run -p 8000:8000 -p 55500:55500 ghcr.io/dl-system/system
```

You can use the application by launching chrome browser and connecting to http://localhost:8000. 

### General

To save your model after docker finishes you can mount a volume to `/system/system/user_data` like so:

#### Linux

```bash
docker run -d \
	--name system \
	--restart unless-stopped \
	-p 8000:8000 \
	-p 55500:55500 \
	-v $(pwd)/data:/system/system/user_data \
	ghcr.io/dl-system/system
```

#### Windows

```bash
docker run -d --name system --restart unless-stopped -p 8000:8000 -p 55500:55500 -v path_to_data:/system/system/user_data ghcr.io/dl-system/system
```

**Please replace `path_to_data!`**

### Accelerated for China

#### Linux

```bash
docker run -d \
    --name system \
    --restart unless-stopped \
    -p 8000:8000 \
    -p 55500:55500 \
    -v $(pwd)/data:/system/system/user_data \
    ghkccr.ccs.tencentyun.com/dovhk/system
```

#### Windows

```bash
docker run -d --name system --restart unless-stopped -p 8000:8000 -p 55500:55500 -v path_to_data:/system/system/user_data hkccr.ccs.tencentyun.com/dovhk/system
```

**Please replace `path_to_data!`**

## Login

To login you can use the following credentials:

| Username | Password |
| -------- | ---- |
| test | testtest |