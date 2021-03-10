filegroup(
  name = "containers",
  srcs = [
    "containers.build_defs"
  ],
  visibility = ['PUBLIC'],
)

subinclude('//:containers')

container_toolchain(name = 'toolchain', use_internal=True)

tarball(
  name = "tools-release",
  srcs = [
    '//:toolchain',
  ],
  out = f'tools-{CONFIG.HOSTOS}_{CONFIG.HOSTARCH}.tar.gz',
  gzip = True,
  flatten = True,
  visibility = ['PUBLIC'],
)