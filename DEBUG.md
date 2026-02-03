The plugin crashes on clean machine - likely OpenSSL dylibs not loading. Let me check if the libraries are bundled correctly:

Run these commands on your dev machine to diagnose:

1. Check what dylibs the plugin links to:

2. Check if OpenSSL dylibs are bundled inside the plugin:

3. Check the archive we just created:

Share the output - we need to verify:

Binary uses @loader_path/../Frameworks/libssl.dylib (not absolute paths)
libssl.dylib and libcrypto.dylib exist in Contents/Frameworks/
