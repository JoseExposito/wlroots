renderers = get_option('renderers')
if 'auto' in renderers and get_option('auto_features').enabled()
	renderers = ['gles2']
elif 'auto' in renderers and get_option('auto_features').disabled()
	renderers = []
endif

wlr_files += files(
	'dmabuf.c',
	'drm_format_set.c',
	'pixel_format.c',
	'swapchain.c',
	'wlr_renderer.c',
	'wlr_texture.c',
)

egl = dependency('egl', required: 'gles2' in renderers)
if egl.found()
	wlr_deps += egl
	wlr_files += files('egl.c')
endif

if 'gles2' in renderers or 'auto' in renderers
	subdir('gles2')
endif

subdir('pixman')

subdir('allocator')
