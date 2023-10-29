project(
    'dbus-activatable-wrapper',
    meson_version: '>= 0.61.0',
    license: 'MIT-0',
)

NAME = get_option('name')
ID = get_option('id')

COMMAND = ''

foreach part : get_option('command')
    COMMAND += '"@0@", '.format(part)
endforeach

CONFIG = {
    'NAME': NAME,
    'ID': ID,
    'COMMAND': COMMAND,
    'BINPATH': get_option('prefix') / get_option('bindir') / NAME,
}

configure_file(
    input: 'wrapper.in',
    output: NAME,
    install_dir: get_option('bindir'),
    configuration: CONFIG,
)

configure_file(
    input: 'desktop.in',
    output: ID + '.desktop',
    install_dir: get_option('datadir') / 'applications',
    configuration: CONFIG,
)

configure_file(
    input: 'service.in',
    output: ID + '.service',
    install_dir: get_option('datadir') / 'dbus-1/services',
    configuration: CONFIG,
)
