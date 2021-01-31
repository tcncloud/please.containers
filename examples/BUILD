subinclude('//:containers')


container_toolchain(name = 'toolchain')


container_pull(
    name = 'ubuntu',
    image = 'ubuntu',
    tag = '20.04',
)


container_flattener(
    name = 'ubuntu_flat',
    baseimage = ":ubuntu"
)