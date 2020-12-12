# Elastic Beanstalk CLI Image

Based on Node 14 Alpine Image

## Usage

`docker run --rm -v "${HOME}/.aws:/root/.aws" -v "$(pwd):/app" wilson208/ebcli`

### Breakdown of that command

- `-v "${HOME}/.aws:/root/.aws"` - Mount stored AWS credentials

-  `-v "$(pwd):/app"` - Mount current directory into the workdir of that container

## Setup Alias

I personally use this by aliasing `eb` to run this image, I have done that by adding this line into my `~/.bash_profile`

`alias eb='docker run --rm -v "${HOME}/.aws:/root/.aws" -v "$(pwd):/app" wilson208/ebcli'`

After you do this, reload your terminal and then use `eb` command as normal, e.g. `eb create`.

## Specify Credentials

The above examples show how this container can be passed pre-configured AWS credentials by mounting the `~/.aws` directory into the container. Alternatively, the standard AWS environment variables can be used as follows:

`docker run --rm -e AWS_ACCESS_KEY_ID={ACCESS KEY} -e AWS_SECRET_ACCESS_KEY={SECRET KEY} -v "$(pwd):/app" wilson208/ebcli'`