subinclude('//:containers')

container_toolchain(name = 'toolchain')

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

container_config(
    name = 'ubuntu_new',
    srcs = { ":ubuntu_flat" },
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