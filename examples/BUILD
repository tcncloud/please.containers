subinclude('//:containers')

container_toolchain(name = 'toolchain', use_internal=True)

filegroup(
    name = 'inject',
    srcs = [
        "testfile1",
        "testfile2",
    ]
)

filegroup(
    name = 'inject_two',
    srcs = [
        "testfile3",
    ]
)

container_pull(
    name = 'ubuntu',
    image = 'ubuntu',
    tag = '20.04',
)

container_flattener(
    name = 'ubuntu_flat',
    baseimage = ":ubuntu",
)

# container_inject just copies a bunch of files from another please target into a separate layer; 
# it may be repeated as many times as there are files
# all files are being copied in the same destination directory
# all files receive the same permissions and owner/group attributes: 755/root/root
# 
# supported arguments (and defaults or suggested values)
# name:                     descriptive
# baseimage: <target>       a previous container_pull or container_flattener target
# srcs: []                  list of targets that contain or generate the files to be copied
# destination: <path>       where to put those files
# timestamp: <unix ts>      required; what to change the access/modified time of the copied files; it MUST be static, otherwise the generated image will change every time the build runs
# owner: 0                  numeric UID string of the owner of the files
# group: 0                  numeric GID string of the group owning the files
# perms: 755                octal value for the permissions


container_inject(
    name = 'ubuntu_files',
    baseimage = ":ubuntu_flat",
    srcs = [ ":inject" ],
    destination = "/opt/foo",
)

container_inject(
    name = 'ubuntu_files_two',
    baseimage = ":ubuntu_files",
    srcs = [ ":inject_two" ],
    destination = "/opt/bar",
)

# container_config runs after inject or flatten and creates the required metadata files for the container
# supported arguments (and defaults/suggested values)
# name: descriptive
# baseimage: <target>       previous container_flatten or container_inject target
# description: ''           what will be the description of the container (optional)
# labels: {}                what labels to associate with the container (optional)
# environment: {}           what environment to provide to the container (optional) - equivalent of the ENV in Dockerfiles
# entrypoint: []            what's the entrypoint of the image (optional)
# command: []               what's the command of the image (optional)
# ports: []                 what to EXPOSE
# timestamp: <unix ts>      required: see container_inject
container_config(
    name = 'ubuntu_new',
    baseimage = ":ubuntu_files_two",
    description = "Foobar image",
    labels = {
        "version": "v1.2.3",
        "foo": "bar",
        "baz": "bla",
    },
    environment = {
        "FOO": "BAR",
    },
    entrypoint = ["/bin/bash"],
    command = [ 
        "-c",
        "foo",
    ],
    ports = [
        "80",
        "443",
    ],
)
# CLOUDSDK_CONFIG has to point to the real $HOME/.config/gcloud directory, otherwise push will fail: please sets HOME to the current build dir
# DOCKER_CONFIG has to point to a $HOME/.docker with configured docker credential/helper for gcr.io cases or some other auth completed already for private repos;
# if the docker-credential-helper is being used, it has to be symlinked into the limited PATH used by please - either /usr/local/bin or /usr/bin
container_push(
    name = 'ubuntu_custom',
    baseimage = ":ubuntu_new",
    repository = 'gcr.io/tcn-cloud-dev/m',
)