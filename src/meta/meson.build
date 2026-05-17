vater_public_headers = [
  'barrier.h',
  'boxes.h',
  'common.h',
  'compositor.h',
  'compositor-vater.h',
  'display.h',
  'group.h',
  'keybindings.h',
  'main.h',
  'meta-backend.h',
  'meta-background.h',
  'meta-background-actor.h',
  'meta-background-content.h',
  'meta-background-group.h',
  'meta-background-image.h',
  'meta-close-dialog.h',
  'meta-cursor-tracker.h',
  'meta-dnd.h',
  'meta-idle-monitor.h',
  'meta-inhibit-shortcuts-dialog.h',
  'meta-launch-context.h',
  'meta-later.h',
  'meta-monitor-manager.h',
  'meta-plugin.h',
  'meta-remote-access-controller.h',
  'meta-selection.h',
  'meta-selection-source.h',
  'meta-selection-source-memory.h',
  'meta-settings.h',
  'meta-shadow-factory.h',
  'meta-shaped-texture.h',
  'meta-sound-player.h',
  'meta-stage.h',
  'meta-startup-notification.h',
  'meta-window-actor.h',
  'meta-window-group.h',
  'meta-window-shape.h',
  'meta-workspace-manager.h',
  'prefs.h',
  'theme.h',
  'types.h',
  'util.h',
  'window.h',
  'workspace.h',
]

if have_wayland
  vater_public_headers += [
    'meta-wayland-client.h',
  ]
endif

if have_x11
  vater_public_headers += [
    'meta-x11-display.h',
    'meta-x11-errors.h',
  ]
endif

install_headers(vater_public_headers,
  subdir: vater_includesubdir
)

vater_public_header_files = files(vater_public_headers)

vater_enum_types = gnome.mkenums('meta-enum-types',
  sources: [vater_public_headers],
  c_template: 'meta-enum-types.c.in',
  h_template: 'meta-enum-types.h.in',
  install_dir: vater_includedir,
  install_header: true,
)

vater_version_array = meson.project_version().split('.')
vater_version_major = vater_version_array[0]
vater_version_minor = vater_version_array[1]
vater_version_micro = vater_version_array[2]

vater_version_cdata = configuration_data()
vater_version_cdata.set('VATER_MAJOR_VERSION',
                         '@0@'.format(vater_version_major))
vater_version_cdata.set('VATER_MINOR_VERSION',
                         '@0@'.format(vater_version_minor))
vater_version_cdata.set('VATER_MICRO_VERSION',
                         '@0@'.format(vater_version_micro))
vater_version_cdata.set('VATER_PLUGIN_API_VERSION',
                         '@0@'.format(vater_plugin_api_version))

vater_version = configure_file(
  input: 'meta-version.h.in',
  output: 'meta-version.h',
  configuration: vater_version_cdata,
  install_dir: vater_includedir,
  install: true,
)
