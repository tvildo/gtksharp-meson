project('gtksharp', ['cs'],
        meson_version: '>=0.59'
        )

dotnet = find_program('dotnet')
warning('Dotnet support is still experimental.')

dotnet_version = run_command(dotnet, ['--version'], check: true)
message('Found dotnet core version ' + dotnet_version.stdout().strip())

prog_install_dir = join_paths(meson.current_build_dir(), 'gtksharp')

dotnet_restore = custom_target('dotnet_restore',
                         output: 'dotnet_restore_out',
                         build_by_default: true,
                         command: [dotnet,
                                   'tool',
                                   'restore'],
                         install: true,
                         install_dir: prog_install_dir,
                         )

cake_build = custom_target('cake_build_out',
                         output: 'cake_build_out',
                         build_by_default: true,
                         command: [dotnet,
                                   'cake',
                                   meson.current_source_dir() + '/build.cake'],
                         install: true,
                         install_dir: prog_install_dir,
                         depends: [dotnet_restore]
                         )
