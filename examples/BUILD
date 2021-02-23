subinclude('//:containers')

container_toolchain(name = 'toolchain')

container_pull(
    name = 'ubuntu',
    image = 'ubuntu',
    tag = '20.04',
)

container_flattener(
    name = 'ubuntu_flat',
    baseimage = ":ubuntu",
    description = "Foobar image",
    labels = {
        "version": "v1.2.3",
        "foo": "bar",
        "baz": "bla",
    },
    environment = {
        "FOO": "BAR",
    },
    entrypoint = "/bin/bash",
    command = [ 
        "-c",
        "foo",
    ],
    ports = [
        "80",
        "443",
    ],
)