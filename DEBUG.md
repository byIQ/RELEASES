The plugin crashes on clean machine - likely OpenSSL dylibs not loading. Let me check if the libraries are bundled correctly:

Run these commands on your dev machine to diagnose:

1. Check what dylibs the plugin links to:

otool -L ~/Library/Audio/Plug-Ins/VST3/AnalogMorphV333.vst3/Contents/MacOS/AnalogMorphV333

2. Check if OpenSSL dylibs are bundled inside the plugin:

ls -la ~/Library/Audio/Plug-Ins/VST3/AnalogMorphV333.vst3/Contents/Frameworks/

3. Check the archive we just created:

unzip -l ~/Downloads/AnalogMorphV333_Installer/vst3.zip | grep -i "dylib\|Frameworks"

Share the output - we need to verify:

Binary uses @loader_path/../Frameworks/libssl.dylib (not absolute paths)
libssl.dylib and libcrypto.dylib exist in Contents/Frameworks/
