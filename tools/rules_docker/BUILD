package(default_visibility=['PUBLIC'])

go_get(
    name = 'rules_docker',
    get = 'github.com/bazelbuild/rules_docker',
    revision = 'v0.15.0',
    install = ['container/go/pkg/...'],
    deps = [
        '//third_party/go/github.com/google:go-containerregistry',
        '//third_party/go/github.com/pkg:errors',
    ]

)
go_get(
    name = 'create_image_config',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/create_image_config'],
    binary = True,
    deps = [':rules_docker']
)

go_get(
    name = 'digester',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/digester'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'extract_config',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/extract_config'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'flattener',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/flattener'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'join_layers',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/join_layers'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'loader',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/loader'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'puller',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/puller'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'pusher',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/pusher'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'update_deps',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/update_deps'],
    binary = True,
    deps = [':rules_docker'],
)

go_get(
    name = 'zipper',
    get = [],
    install = ['github.com/bazelbuild/rules_docker/container/go/cmd/zipper'],
    binary = True,
    deps = [':rules_docker'],
)
