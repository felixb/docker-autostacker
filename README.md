# docker-autostacker

Run [autostacker24](https://github.com/AutoScout24/autostacker24) w/o installing ruby on your system.

## Usage

Run the container like this:

```bash
docker run \
    -v "${PWD}:/workdir:ro" \         # <-- this mounts your current directory inside the container's work dir
    -v "${HOME}/.aws:/.aws:ro" \      # <-- this mounts your aws credentials inside the container's home dir
    -e AWS_PROFILE=some-aws-profile \ # <-- choose your aws profile
    felixb/autostacker \
    update \                          # <-- run any autostacker24 command
        --stack some-stack \
        --template some-template.yaml
```

You might want to add the following function to your `.bashrc` or similar to allow even easier usage:

```bash
function autostacker() {
    docker run \
        --rm \
        -v "${PWD}:/workdir:ro" \
        -v "${HOME}/.aws:/.aws:ro" \
        -e "AWS_PROFILE=${AWS_PROFILE}" \
        -e "AWS_REGION=${AWS_REGION}" \
        felixb/autostacker \
        "${@}"
}
```

