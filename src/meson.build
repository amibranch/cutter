
cutter_include_dirs = include_directories([
  '.',
  'core',
  'widgets',
  'common',
  'dialogs',
  join_paths('dialogs', 'preferences'),
  'menus',
  ])

common_cpp_args = [ '-DCUTTER_ENABLE_PYTHON', ]


### CutterConfig.h.in
cutterconfig_data = configuration_data()
cutterconfig_data.set('CUTTER_VERSION_MAJOR', cutter_version_major)
cutterconfig_data.set('CUTTER_VERSION_MINOR', cutter_version_minor)
cutterconfig_data.set('CUTTER_VERSION_PATCH', cutter_version_patch)
cutterconfig_data.set('CUTTER_VERSION_FULL', meson.project_version())
cutterconfig_data.set('CUTTER_EXTRA_PLUGIN_DIRS', get_option('extra_plugin_dir'))
cutterconfig = configure_file(
  input : 'CutterConfig.h.in',
  output: 'CutterConfig.h',
  configuration: cutterconfig_data,
  )

ui_headers = []

qt6 = import('qt6', required: true)

foreach ui : [
  join_paths('dialogs', 'IncrementDecrementDialog.ui'),
  join_paths('dialogs', 'EditInstructionDialog.ui'),
  join_paths('dialogs', 'RizinPluginsDialog.ui'),
  join_paths('dialogs', 'Base64EnDecodedWriteDialog.ui'),
  join_paths('dialogs', 'VersionInfoDialog.ui'),
  join_paths('dialogs', 'BreakpointsDialog.ui'),
  join_paths('dialogs', 'GlibcHeapInfoDialog.ui'),
  join_paths('dialogs', 'RemoteDebugDialog.ui'),
  join_paths('dialogs', 'EditFunctionDialog.ui'),
  join_paths('dialogs', 'NativeDebugDialog.ui'),
  join_paths('dialogs', 'AttachProcDialog.ui'),
  join_paths('dialogs', 'FlagDialog.ui'),
  join_paths('dialogs', 'SetToDataDialog.ui'),
  join_paths('dialogs', 'GlibcHeapBinsDialog.ui'),
  join_paths('dialogs', 'RizinTaskDialog.ui'),
  join_paths('dialogs', 'AboutDialog.ui'),
  join_paths('dialogs', 'DuplicateFromOffsetDialog.ui'),
  join_paths('dialogs', 'GlobalVariableDialog.ui'),
  join_paths('dialogs', 'EditStringDialog.ui'),
  join_paths('dialogs', 'CommentsDialog.ui'),
  join_paths('dialogs', 'HexdumpRangeDialog.ui'),
  join_paths('dialogs', 'ArenaInfoDialog.ui'),
  join_paths('dialogs', 'TypesInteractionDialog.ui'),
  join_paths('dialogs', 'NewFileDialog.ui'),
  join_paths('dialogs', 'InitialOptionsDialog.ui'),
  join_paths('dialogs', 'EditMethodDialog.ui'),
  join_paths('dialogs', 'WelcomeDialog.ui'),
  join_paths('dialogs', 'LayoutManager.ui'),
  join_paths('dialogs', 'MapFileDialog.ui'),
  join_paths('dialogs', 'EditVariablesDialog.ui'),
  join_paths('dialogs', 'AsyncTaskDialog.ui'),
  join_paths('dialogs', 'XrefsDialog.ui'),
  join_paths('core', 'MainWindow.ui'),
  join_paths('widgets', 'RegisterRefsWidget.ui'),
  join_paths('widgets', 'TypesWidget.ui'),
  join_paths('widgets', 'EntrypointWidget.ui'),
  join_paths('widgets', 'Dashboard.ui'),
  join_paths('widgets', 'FlagsWidget.ui'),
  join_paths('widgets', 'CutterTreeView.ui'),
  join_paths('widgets', 'ComboQuickFilterView.ui'),
  join_paths('widgets', 'DecompilerWidget.ui'),
  join_paths('widgets', 'GlobalsWidget.ui'),
  join_paths('widgets', 'StackWidget.ui'),
  join_paths('widgets', 'QuickFilterView.ui'),
  join_paths('widgets', 'HexdumpWidget.ui'),
  join_paths('widgets', 'ColorPicker.ui'),
  join_paths('widgets', 'HeapDockWidget.ui'),
  join_paths('widgets', 'ProcessesWidget.ui'),
  join_paths('widgets', 'RizinGraphWidget.ui'),
  join_paths('widgets', 'RegistersWidget.ui'),
  join_paths('widgets', 'StringsWidget.ui'),
  join_paths('widgets', 'VTablesWidget.ui'),
  join_paths('widgets', 'BacktraceWidget.ui'),
  join_paths('widgets', 'ThreadsWidget.ui'),
  join_paths('widgets', 'SearchWidget.ui'),
  join_paths('widgets', 'SdbWidget.ui'),
  join_paths('widgets', 'ConsoleWidget.ui'),
  join_paths('widgets', 'GlibcHeapWidget.ui'),
  join_paths('widgets', 'BreakpointWidget.ui'),
  join_paths('widgets', 'ListDockWidget.ui'),
  join_paths('widgets', 'FlirtWidget.ui'),
  join_paths('dialogs', 'preferences', 'ColorThemeEditDialog.ui'),
  join_paths('dialogs', 'preferences', 'AnalysisOptionsWidget.ui'),
  join_paths('dialogs', 'preferences', 'GraphOptionsWidget.ui'),
  join_paths('dialogs', 'preferences', 'AppearanceOptionsWidget.ui'),
  join_paths('dialogs', 'preferences', 'AsmOptionsWidget.ui'),
  join_paths('dialogs', 'preferences', 'DebugOptionsWidget.ui'),
  join_paths('dialogs', 'preferences', 'InitializationFileEditor.ui'),
  join_paths('dialogs', 'preferences', 'PreferencesDialog.ui'),
  join_paths('tools', 'basefind', 'BaseFindSearchDialog.ui'),
  join_paths('tools', 'basefind', 'BaseFindDialog.ui'),
  join_paths('tools', 'basefind', 'BaseFindResultsDialog.ui'),
  ]

  ui_headers += qt6.compile_ui(sources: ui, )

endforeach

rc_sources = []

foreach rc : [
  'resources.qrc',
  join_paths('themes', 'native', 'native.qrc'),
  join_paths('themes', 'qdarkstyle', 'dark.qrc'),
  join_paths('themes', 'midnight', 'midnight.qrc'),
  join_paths('themes', 'lightstyle', 'light.qrc'),
  ]

  rc_sources += qt6.compile_resources(sources: rc)
endforeach


cutter_common_headers = [
  join_paths('common', 'RefreshDeferrer.h'),
  join_paths('common', 'CommandTask.h'),
  join_paths('common', 'SelectionHighlight.h'),
  join_paths('common', 'StringsTask.h'),
  join_paths('common', 'AddressableItemModel.h'),
  join_paths('common', 'TempConfig.h'),
  join_paths('common', 'LinkedListPool.h'),
  join_paths('common', 'Decompiler.h'),
  join_paths('common', 'DecompilerHighlighter.h'),
  join_paths('common', 'ProgressIndicator.h'),
  join_paths('common', 'RunScriptTask.h'),
  join_paths('common', 'SyntaxHighlighter.h'),
  join_paths('common', 'MdHighlighter.h'),
  join_paths('common', 'InitialOptions.h'),
  join_paths('common', 'UpdateWorker.h'),
  join_paths('common', 'BasicBlockHighlighter.h'),
  join_paths('common', 'Highlighter.h'),
  join_paths('common', 'PythonManager.h'),
  join_paths('common', 'CutterLayout.h'),
  join_paths('common', 'AsyncTask.h'),
  join_paths('common', 'SettingsUpgrade.h'),
  join_paths('common', 'RichTextPainter.h'),
  join_paths('common', 'Helpers.h'),
  join_paths('common', 'JsonModel.h'),
  join_paths('common', 'Json.h'),
  join_paths('common', 'Colors.h'),
  join_paths('common', 'ColorThemeWorker.h'),
  join_paths('common', 'ResourcePaths.h'),
  join_paths('common', 'RizinTask.h'),
  join_paths('common', 'SvgIconEngine.h'),
  join_paths('common', 'CutterSeekable.h'),
  join_paths('common', 'IOModesController.h'),
  join_paths('common', 'BinaryTrees.h'),
  join_paths('common', 'AnalysisTask.h'),
  join_paths('common', 'Configuration.h'),
  join_paths('common', 'Metrics.h'),
  join_paths('common', 'FunctionsTask.h'),
  join_paths('common', 'HighDpiPixmap.h'),
  join_paths('common', 'PythonAPI.h'),
  join_paths('common', 'DirectionalComboBox.h'),
  join_paths('common', 'QtResImporter.h'),
  join_paths('common', 'BasicInstructionHighlighter.h'),
  join_paths('common', 'BugReporting.h'),
  join_paths('common', 'DisassemblyPreview.h'),
  join_paths('common', 'CachedFontMetrics.h'),
  ]

cutter_dialog_headers = [
  join_paths('dialogs', 'GlibcHeapInfoDialog.h'),
  join_paths('dialogs', 'InitialOptionsDialog.h'),
  join_paths('dialogs', 'EditInstructionDialog.h'),
  join_paths('dialogs', 'GlobalVariableDialog.h'),
  join_paths('dialogs', 'FlagDialog.h'),
  join_paths('dialogs', 'AsyncTaskDialog.h'),
  join_paths('dialogs', 'LayoutManager.h'),
  join_paths('dialogs', 'SetToDataDialog.h'),
  join_paths('dialogs', 'RizinPluginsDialog.h'),
  join_paths('dialogs', 'WriteCommandsDialogs.h'),
  join_paths('dialogs', 'XrefsDialog.h'),
  join_paths('dialogs', 'EditFunctionDialog.h'),
  join_paths('dialogs', 'EditMethodDialog.h'),
  join_paths('dialogs', 'NativeDebugDialog.h'),
  join_paths('dialogs', 'TypesInteractionDialog.h'),
  join_paths('dialogs', 'MultitypeFileSaveDialog.h'),
  join_paths('dialogs', 'AboutDialog.h'),
  join_paths('dialogs', 'VersionInfoDialog.h'),
  join_paths('dialogs', 'WelcomeDialog.h'),
  join_paths('dialogs', 'ArenaInfoDialog.h'),
  join_paths('dialogs', 'CommentsDialog.h'),
  join_paths('dialogs', 'BreakpointsDialog.h'),
  join_paths('dialogs', 'NewFileDialog.h'),
  join_paths('dialogs', 'EditVariablesDialog.h'),
  join_paths('dialogs', 'AttachProcDialog.h'),
  join_paths('dialogs', 'MapFileDialog.h'),
  join_paths('dialogs', 'HexdumpRangeDialog.h'),
  join_paths('dialogs', 'EditStringDialog.h'),
  join_paths('dialogs', 'RemoteDebugDialog.h'),
  join_paths('dialogs', 'RizinTaskDialog.h'),
  join_paths('dialogs', 'GlibcHeapBinsDialog.h'),
  join_paths('dialogs', 'preferences', 'ColorThemeEditDialog.h'),
  join_paths('dialogs', 'preferences', 'AnalysisOptionsWidget.h'),
  join_paths('dialogs', 'preferences', 'PreferencesDialog.h'),
  join_paths('dialogs', 'preferences', 'InitializationFileEditor.h'),
  join_paths('dialogs', 'preferences', 'DebugOptionsWidget.h'),
  join_paths('dialogs', 'preferences', 'PluginsOptionsWidget.h'),
  join_paths('dialogs', 'preferences', 'AppearanceOptionsWidget.h'),
  join_paths('dialogs', 'preferences', 'GraphOptionsWidget.h'),
  join_paths('dialogs', 'preferences', 'AsmOptionsWidget.h'),
  #join_paths('dialogs', 'preferences', 'PreferenceCategory.h'),
  ]

cutter_widgets_headers = [
  join_paths('widgets', 'ColorThemeListView.h'),
  join_paths('widgets', 'ImportsWidget.h'),
  join_paths('widgets', 'CutterDockWidget.h'),
  join_paths('widgets', 'BacktraceWidget.h'),
  join_paths('widgets', 'RelocsWidget.h'),
  join_paths('widgets', 'TypesWidget.h'),
  join_paths('widgets', 'RizinGraphWidget.h'),
  #join_paths('widgets', 'WidgetShortcuts.h'),
  join_paths('widgets', 'HexdumpWidget.h'),
  join_paths('widgets', 'ThreadsWidget.h'),
  join_paths('widgets', 'StackWidget.h'),
  join_paths('widgets', 'CallGraph.h'),
  join_paths('widgets', 'MemoryDockWidget.h'),
  join_paths('widgets', 'FunctionsWidget.h'),
  join_paths('widgets', 'AddressableDockWidget.h'),
  join_paths('widgets', 'Omnibar.h'),
  join_paths('widgets', 'SdbWidget.h'),
  join_paths('widgets', 'OverviewWidget.h'),
  join_paths('widgets', 'DebugActions.h'),
  join_paths('widgets', 'SearchWidget.h'),
  join_paths('widgets', 'SectionsWidget.h'),
  join_paths('widgets', 'ConsoleWidget.h'),
  join_paths('widgets', 'CutterGraphView.h'),
  join_paths('widgets', 'CutterTreeWidget.h'),
  join_paths('widgets', 'GraphWidget.h'),
  join_paths('widgets', 'ListDockWidget.h'),
  join_paths('widgets', 'FlirtWidget.h'),
  join_paths('widgets', 'RegistersWidget.h'),
  join_paths('widgets', 'GlibcHeapWidget.h'),
  #join_paths('widgets', 'BoolToggleDelegate.h'),
  join_paths('widgets', 'DecompilerWidget.h'),
  join_paths('widgets', 'CommentsWidget.h'),
  join_paths('widgets', 'ColorThemeComboBox.h'),
  join_paths('widgets', 'QuickFilterView.h'),
  join_paths('widgets', 'VTablesWidget.h'),
  join_paths('widgets', 'ClassesWidget.h'),
  join_paths('widgets', 'HeapBinsGraphView.h'),
  join_paths('widgets', 'GlobalsWidget.h'),
  join_paths('widgets', 'ComboQuickFilterView.h'),
  join_paths('widgets', 'ExportsWidget.h'),
  #join_paths('widgets', 'GraphGridLayout.h'),
  join_paths('widgets', 'ProcessesWidget.h'),
  #join_paths('widgets', 'AddressableItemList.h'),
  join_paths('widgets', 'FlagsWidget.h'),
  join_paths('widgets', 'Dashboard.h'),
  #join_paths('widgets', 'GraphvizLayout.h'),
  #join_paths('widgets', 'GraphLayout.h'),
  join_paths('widgets', 'HeadersWidget.h'),
  join_paths('widgets', 'DisassemblyWidget.h'),
  join_paths('widgets', 'ColorPicker.h'),
  join_paths('widgets', 'SegmentsWidget.h'),
  join_paths('widgets', 'SimpleTextGraphView.h'),
  join_paths('widgets', 'GraphView.h'),
  join_paths('widgets', 'StringsWidget.h'),
  join_paths('widgets', 'DisassemblerGraphView.h'),
  join_paths('widgets', 'ResourcesWidget.h'),
  join_paths('widgets', 'HeapDockWidget.h'),
  join_paths('widgets', 'VisualNavbar.h'),
  join_paths('widgets', 'RegisterRefsWidget.h'),
  join_paths('widgets', 'OverviewView.h'),
  join_paths('widgets', 'SymbolsWidget.h'),
  join_paths('widgets', 'BreakpointWidget.h'),
  #join_paths('widgets', 'GraphHorizontalAdapter.h'),
  join_paths('widgets', 'HexWidget.h'),
  join_paths('widgets', 'EntrypointWidget.h'),
  join_paths('widgets', 'CutterTreeView.h'),
  join_paths('widgets', 'MemoryMapWidget.h'),
  ]

cutter_core_headers = [
  #join_paths('core', 'CutterDescriptions.h'),
  join_paths('core', 'Basefind.h'),
  #join_paths('core', 'CutterCommon.h'),
  join_paths('core', 'MainWindow.h'),
  #join_paths('core', 'RizinCpp.h'),
  #join_paths('core', 'CutterJson.h'),
  join_paths('core', 'Cutter.h'),
  ]

cutter_menus_headers = [
  join_paths('menus', 'DecompilerContextMenu.h'),
  join_paths('menus', 'AddressableItemContextMenu.h'),
  join_paths('menus', 'DisassemblyContextMenu.h'),
  join_paths('menus', 'FlirtContextMenu.h'),
  ]

cutter_plugins_headers = [
  join_paths('plugins', 'PluginManager.h'),
  ]

cutter_tools_headers = [
  join_paths('tools', 'basefind', 'BaseFindResultsDialog.h'),
  join_paths('tools', 'basefind', 'BaseFindSearchDialog.h'),
  join_paths('tools', 'basefind', 'BaseFindDialog.h'),
  ]

cutter_headers = ['CutterApplication.h'] + cutter_common_headers + cutter_dialog_headers + cutter_widgets_headers + cutter_core_headers + cutter_menus_headers + cutter_plugins_headers + cutter_tools_headers

moc_sources = []

foreach moc : cutter_headers
  moc_sources += qt6.compile_moc(headers: moc, extra_args: common_cpp_args, )
endforeach

#ui_headers += qt6.compile_ui(sources: 'widgets/VTablesWidget.ui', preserve_paths: true)
#ui_mainwindow = [
#  ]

cutter_common_source = [
  join_paths('common', 'Helpers.cpp'),
  join_paths('common', 'HighDpiPixmap.cpp'),
  join_paths('common', 'BasicBlockHighlighter.cpp'),
  join_paths('common', 'SyntaxHighlighter.cpp'),
  join_paths('common', 'DirectionalComboBox.cpp'),
  join_paths('common', 'SettingsUpgrade.cpp'),
  join_paths('common', 'BasicInstructionHighlighter.cpp'),
  join_paths('common', 'ColorThemeWorker.cpp'),
  join_paths('common', 'AddressableItemModel.cpp'),
  join_paths('common', 'UpdateWorker.cpp'),
  join_paths('common', 'TempConfig.cpp'),
  join_paths('common', 'IOModesController.cpp'),
  join_paths('common', 'DisassemblyPreview.cpp'),
  join_paths('common', 'ResourcePaths.cpp'),
  join_paths('common', 'CutterSeekable.cpp'),
  join_paths('common', 'QtResImporter.cpp'),
  join_paths('common', 'MdHighlighter.cpp'),
  join_paths('common', 'PythonManager.cpp'),       # ENABLE_PYTHON
  join_paths('common', 'RichTextPainter.cpp'),
  join_paths('common', 'PythonAPI.cpp'),           # ENABLE_PYTHON
  join_paths('common', 'BugReporting.cpp'),
  join_paths('common', 'RizinTask.cpp'),
  join_paths('common', 'CutterLayout.cpp'),
  join_paths('common', 'CommandTask.cpp'),
  join_paths('common', 'SvgIconEngine.cpp'),
  join_paths('common', 'AnalysisTask.cpp'),
  join_paths('common', 'JsonModel.cpp'),
  join_paths('common', 'Colors.cpp'),
  join_paths('common', 'ProgressIndicator.cpp'),
  join_paths('common', 'Decompiler.cpp'),
  join_paths('common', 'DecompilerHighlighter.cpp'),
  join_paths('common', 'RefreshDeferrer.cpp'),
  join_paths('common', 'AsyncTask.cpp'),
  join_paths('common', 'RunScriptTask.cpp'),
  join_paths('common', 'Configuration.cpp'),
  join_paths('common', 'SelectionHighlight.cpp'),
  join_paths('common', 'Highlighter.cpp'),
  ]

cutter_dialogs_source = [
  join_paths('dialogs', 'LayoutManager.cpp'),
  join_paths('dialogs', 'CommentsDialog.cpp'),
  join_paths('dialogs', 'RizinTaskDialog.cpp'),
  join_paths('dialogs', 'AboutDialog.cpp'),
  join_paths('dialogs', 'MapFileDialog.cpp'),
  join_paths('dialogs', 'RemoteDebugDialog.cpp'),
  join_paths('dialogs', 'AttachProcDialog.cpp'),
  join_paths('dialogs', 'EditVariablesDialog.cpp'),
  join_paths('dialogs', 'NewFileDialog.cpp'),
  join_paths('dialogs', 'WelcomeDialog.cpp'),
  join_paths('dialogs', 'VersionInfoDialog.cpp'),
  join_paths('dialogs', 'XrefsDialog.cpp'),
  join_paths('dialogs', 'WriteCommandsDialogs.cpp'),
  join_paths('dialogs', 'InitialOptionsDialog.cpp'),
  join_paths('dialogs', 'EditInstructionDialog.cpp'),
  join_paths('dialogs', 'FlagDialog.cpp'),
  join_paths('dialogs', 'ArenaInfoDialog.cpp'),
  join_paths('dialogs', 'SetToDataDialog.cpp'),
  join_paths('dialogs', 'HexdumpRangeDialog.cpp'),
  join_paths('dialogs', 'MultitypeFileSaveDialog.cpp'),
  join_paths('dialogs', 'GlobalVariableDialog.cpp'),
  join_paths('dialogs', 'BreakpointsDialog.cpp'),
  join_paths('dialogs', 'EditStringDialog.cpp'),
  join_paths('dialogs', 'EditFunctionDialog.cpp'),
  join_paths('dialogs', 'GlibcHeapBinsDialog.cpp'),
  join_paths('dialogs', 'NativeDebugDialog.cpp'),
  join_paths('dialogs', 'EditMethodDialog.cpp'),
  join_paths('dialogs', 'GlibcHeapInfoDialog.cpp'),
  join_paths('dialogs', 'AsyncTaskDialog.cpp'),
  join_paths('dialogs', 'RizinPluginsDialog.cpp'),
  join_paths('dialogs', 'TypesInteractionDialog.cpp'),
  join_paths('dialogs', 'preferences', 'PluginsOptionsWidget.cpp'),
  join_paths('dialogs', 'preferences', 'AppearanceOptionsWidget.cpp'),
  join_paths('dialogs', 'preferences', 'InitializationFileEditor.cpp'),
  join_paths('dialogs', 'preferences', 'PreferencesDialog.cpp'),
  join_paths('dialogs', 'preferences', 'GraphOptionsWidget.cpp'),
  join_paths('dialogs', 'preferences', 'DebugOptionsWidget.cpp'),
  join_paths('dialogs', 'preferences', 'AnalysisOptionsWidget.cpp'),
  join_paths('dialogs', 'preferences', 'PreferenceCategory.cpp'),
  join_paths('dialogs', 'preferences', 'ColorThemeEditDialog.cpp'),
  join_paths('dialogs', 'preferences', 'AsmOptionsWidget.cpp'),
  ]

cutter_widgets_source = [
  join_paths('widgets', 'GraphView.cpp'),
  join_paths('widgets', 'StringsWidget.cpp'),
  join_paths('widgets', 'GraphGridLayout.cpp'),
  join_paths('widgets', 'OverviewWidget.cpp'),
  join_paths('widgets', 'BacktraceWidget.cpp'),
  join_paths('widgets', 'ComboQuickFilterView.cpp'),
  join_paths('widgets', 'QuickFilterView.cpp'),
  join_paths('widgets', 'VisualNavbar.cpp'),
  join_paths('widgets', 'ExportsWidget.cpp'),
  join_paths('widgets', 'AddressableDockWidget.cpp'),
  join_paths('widgets', 'ImportsWidget.cpp'),
  join_paths('widgets', 'CommentsWidget.cpp'),
  join_paths('widgets', 'CutterGraphView.cpp'),
  join_paths('widgets', 'OverviewView.cpp'),
  join_paths('widgets', 'CutterTreeWidget.cpp'),
  join_paths('widgets', 'DecompilerWidget.cpp'),
  join_paths('widgets', 'HeapBinsGraphView.cpp'),
  join_paths('widgets', 'BoolToggleDelegate.cpp'),
  join_paths('widgets', 'SectionsWidget.cpp'),
  join_paths('widgets', 'GraphHorizontalAdapter.cpp'),
  join_paths('widgets', 'HexdumpWidget.cpp'),
  join_paths('widgets', 'GraphWidget.cpp'),
  join_paths('widgets', 'RelocsWidget.cpp'),
  join_paths('widgets', 'DisassemblyWidget.cpp'),
  join_paths('widgets', 'ListDockWidget.cpp'),
  join_paths('widgets', 'CutterTreeView.cpp'),
  join_paths('widgets', 'FlagsWidget.cpp'),
  join_paths('widgets', 'ResourcesWidget.cpp'),
  join_paths('widgets', 'HeadersWidget.cpp'),
  join_paths('widgets', 'GlibcHeapWidget.cpp'),
  join_paths('widgets', 'MemoryDockWidget.cpp'),
  join_paths('widgets', 'RizinGraphWidget.cpp'),
  join_paths('widgets', 'FlirtWidget.cpp'),
  join_paths('widgets', 'DisassemblerGraphView.cpp'),
  join_paths('widgets', 'VTablesWidget.cpp'),
  join_paths('widgets', 'CutterDockWidget.cpp'),
  join_paths('widgets', 'ThreadsWidget.cpp'),
  join_paths('widgets', 'BreakpointWidget.cpp'),
  join_paths('widgets', 'DebugActions.cpp'),
  join_paths('widgets', 'SymbolsWidget.cpp'),
  join_paths('widgets', 'GraphvizLayout.cpp'),
  join_paths('widgets', 'EntrypointWidget.cpp'),
  join_paths('widgets', 'SimpleTextGraphView.cpp'),
  join_paths('widgets', 'HeapDockWidget.cpp'),
  join_paths('widgets', 'SearchWidget.cpp'),
  join_paths('widgets', 'FunctionsWidget.cpp'),
  join_paths('widgets', 'ProcessesWidget.cpp'),
  join_paths('widgets', 'RegisterRefsWidget.cpp'),
  join_paths('widgets', 'GlobalsWidget.cpp'),
  join_paths('widgets', 'ConsoleWidget.cpp'),
  join_paths('widgets', 'SdbWidget.cpp'),
  join_paths('widgets', 'ColorPicker.cpp'),
  join_paths('widgets', 'Dashboard.cpp'),
  join_paths('widgets', 'CallGraph.cpp'),
  join_paths('widgets', 'RegistersWidget.cpp'),
  join_paths('widgets', 'TypesWidget.cpp'),
  join_paths('widgets', 'HexWidget.cpp'),
  join_paths('widgets', 'ClassesWidget.cpp'),
  join_paths('widgets', 'Omnibar.cpp'),
  join_paths('widgets', 'SegmentsWidget.cpp'),
  join_paths('widgets', 'StackWidget.cpp'),
  join_paths('widgets', 'ColorThemeListView.cpp'),
  join_paths('widgets', 'ColorThemeComboBox.cpp'),
  join_paths('widgets', 'MemoryMapWidget.cpp'),
  ]

cutter_tools_sources = [
  join_paths('tools', 'basefind', 'BaseFindResultsDialog.cpp'),
  join_paths('tools', 'basefind', 'BaseFindSearchDialog.cpp'),
  join_paths('tools', 'basefind', 'BaseFindDialog.cpp'),
  ]

cutter_source = [
  'Main.cpp',
  'CutterApplication.cpp',
  ] + cutter_common_source + cutter_dialogs_source + cutter_widgets_source + moc_sources + \
      cutter_tools_sources + rc_sources + [
  'core/Basefind.cpp',
  'core/RizinCpp.cpp',
  'core/MainWindow.cpp',
  'core/Cutter.cpp',
  'core/CutterJson.cpp',
  'plugins/PluginManager.cpp',
  join_paths('menus', 'DecompilerContextMenu.cpp'),
  join_paths('menus', 'FlirtContextMenu.cpp'),
  join_paths('menus', 'AddressableItemContextMenu.cpp'),
  join_paths('menus', 'DisassemblyContextMenu.cpp'),
  ]

rz_exe_cpp_args = ['-fPIC', ] + common_cpp_args

if get_option('ghidra-plugin')

  cutter_dep = declare_dependency(
    include_directories: cutter_include_dirs,
    dependencies: qt6_deps + rz_deps,
    )

  meson.override_dependency('libcutter', cutter_dep)
  if false
  meson.override_dependency('rz_syscall', rz_syscall_dep)
  meson.override_dependency('rz_reg', rz_reg_dep)
  meson.override_dependency('rz_core', rz_core_dep)
  meson.override_dependency('rz_flag', rz_flag_dep)
  meson.override_dependency('rz_debug', rz_debug_dep)
  meson.override_dependency('rz_socket', rz_socket_dep)
  meson.override_dependency('rz_analysis', rz_analysis_dep)
  meson.override_dependency('rz_diff', rz_diff_dep)
  meson.override_dependency('rz_cons', rz_cons_dep)
  meson.override_dependency('rz_bin', rz_bin_dep)
  meson.override_dependency('rz_egg', rz_egg_dep)
  meson.override_dependency('rz_type', rz_type_dep)
  meson.override_dependency('rz_sign', rz_sign_dep)
  meson.override_dependency('rz_demangler', rz_demangler_dep)
  meson.override_dependency('rz_il', rz_il_dep)
  meson.override_dependency('rz_parse', rz_parse_dep)
  meson.override_dependency('rz_config', rz_config_dep)
  meson.override_dependency('rz_bp', rz_bp_dep)
  meson.override_dependency('rz_util', rz_util_dep)
  meson.override_dependency('rz_main', rz_main_dep)
  meson.override_dependency('rz_hash', rz_hash_dep)
  meson.override_dependency('rz_search', rz_search_dep)
  meson.override_dependency('rz_lang', rz_lang_dep)
  meson.override_dependency('rz_io', rz_io_dep)
  meson.override_dependency('rz_crypto', rz_crypto_dep)
  meson.override_dependency('rz_magic', rz_magic_dep)
  meson.override_dependency('rz_asm', rz_asm_dep)
  endif

  rz_ghidra_subproj = subproject('rz-ghidra', default_options: { 'cutter-plugin': true })
  cutter_ghidra_plugin_dep = rz_ghidra_subproj.get_variable('cutter_ghidra_dep')
  rz_ghidra_dep = rz_ghidra_subproj.get_variable('rz_ghidra_dep')
  rz_deps += cutter_ghidra_plugin_dep
  rz_deps += rz_ghidra_dep
  rz_exe_cpp_args += [ '-DCUTTER_RZGHIDRA_STATIC', ]

endif

cutter = executable('cutter',
           cutter_source,
           cutterconfig,
           dependencies: qt6_deps + rz_deps + python_dep + graphviz_deps + [
             declare_dependency( sources: ui_headers),
             declare_dependency( sources: cutter_headers),
             ],
           include_directories: cutter_include_dirs,
           install: true,
           pie: true,
           cpp_args: rz_exe_cpp_args,
           )

