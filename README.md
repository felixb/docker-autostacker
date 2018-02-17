# docker-autostacker

Run autostacker24 w/o installing ruby on your system.

## Usage

Run the container like this:

```bash
docker run \
    -v "${PWD}:/workdir:ro" \         # <-- this mounts your current directory inside the container's work dir
    -v "${HOME}/.aws:/.aws:ro" \      # <-- this mounts your aws credentials inside the container's home dir
    -e AWS_PROFILE=some-aws-profile \ # <-- choose your aws profile
    update \                          # <-- run any autostacker24 command
        --stack some-stack \
        --template some-template.yaml
```