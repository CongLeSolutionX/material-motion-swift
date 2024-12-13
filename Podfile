# Add this line to the top to suppress the master specs repo warning
warn_for_unused_master_specs_repo = false

workspace 'MaterialMotion.xcworkspace'
use_frameworks!

target "MaterialMotionCatalog" do
  platform :ios, '17.0'  # Specify platform and minimum iOS version here
  pod 'CatalogByConvention'
  pod 'MaterialMotion', :path => './'

  project 'examples/apps/Catalog/MaterialMotionCatalog.xcodeproj'
end

target "UnitTests" do
  platform :ios, '17.0' # Specify platform and minimum iOS version here
  pod 'MaterialMotion', :path => './'

  project 'examples/apps/Catalog/MaterialMotionCatalog.xcodeproj'
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |configuration|
      configuration.build_settings['SWIFT_VERSION'] = "5.0"
      if target.name.start_with?("Material")
        configuration.build_settings['WARNING_CFLAGS'] = "$(inherited) -Wall -Wcast-align -Wconversion -Werror -Wextra -Wimplicit-atomic-properties -Wmissing-prototypes -Wno-sign-conversion -Wno-unused-parameter -Woverlength-strings -Wshadow -Wstrict-selector-match -Wundeclared-selector -Wunreachable-code"
      end
    end
  end
end