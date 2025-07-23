# DevOps Demo Project

This is a project for week#1 learning course "Devops and Kubernetes"
This is a simple Go web server that serves static HTML/SVG content with animations.

## Building and Running Locally

### Build the Server

```bash
go build -o bin/app src/main.go
```

The compiled binary will be available at `bin/app`.

### Run the Server

```bash
bin/app
```

### Test the Server

```bash
curl localhost:8080
```

You can also open `http://localhost:8080` in your web browser to see the SVG animations.

### Initialize Go Dependencies

```bash
cd src
go mod init demo
```

## Docker Support

### Build the Docker Image

```bash
docker build .
```

### Run the Docker Container

Replace the image ID with your actual image ID:

```bash
docker run -p 8080:8080 <image-id>
```

Example:

```bash
docker run -p 8080:8080 sha256:eb51004b45da3665d05b64a688d2f3b4edf9547600ac5a70b3c71cea533d54cc
```

## Docker Hub Integration

### Tag the Docker Image

```bash
docker tag <image-id> <dockerhub-username>/devops-demo:<tag>
```

Example:

```bash
docker tag eb51004b45da blackbird1989/devops-demo:v1.0.0
```

Where:
- `eb51004b45da` - image ID
- `blackbird1989` - Docker Hub account
- `devops-demo` - Docker Hub repository
- `:v1.0.0` - tag version

### Push to Docker Hub

```bash
docker push <dockerhub-username>/devops-demo:<tag>
```

Example:

```bash
docker push blackbird1989/devops-demo:v1.0.0
```

## Project Structure

- `src/main.go` - Go web server code
- `src/go.mod` - Go module definition
- `html/` - Static HTML and SVG files for the web interface
- `Dockerfile` - Multi-stage Docker build configuration

## Technical Details

The server is a simple Go application that serves static files from the `html` directory on port 8080. The Docker image is built using a multi-stage build process to create a minimal container.