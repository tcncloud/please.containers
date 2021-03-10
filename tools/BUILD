tarball(
    name = 'tools',
    srcs = [
        '//tools/rules_docker:create_image_config',
        '//tools/rules_docker:digester',
        '//tools/rules_docker:extract_config',
        '//tools/rules_docker:flattener',
        '//tools/rules_docker:join_layers',
        '//tools/rules_docker:loader',
        '//tools/rules_docker:puller',
        '//tools/rules_docker:pusher',
        '//tools/rules_docker:update_deps',
        '//tools/rules_docker:zipper',
        '//tools/sha256',
    ],
    out = f'tools-{CONFIG.OS}_{CONFIG.ARCH}.tar.gz',
    flatten = True,
    visibility =['PUBLIC']
)