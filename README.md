# Building SailfishOS 4.5 for Redmi Note 8

## Build errors
Before building anything with build_package make sure to run
```
sb2 -t $VENDOR-$DEVICE-$PORT_ARCH -msdk-install -R zypper in ccache
sb2 -t $VENDOR-$DEVICE-$PORT_ARCH -m sdk-install -R zypper -n rm bluez5-configs-mer
```

To build --version the following are needed
```
sdk-assistant maintain $VENDOR-$DEVICE-$PORT_ARCH zypper -n --plus-repo $ANDROID_ROOT/droid-local-repo/ginkgo/ install --allow-unsigned-rpm droid-hal-ginkgo droid-hal-ginkgo-kernel
sdk-assistant maintain $VENDOR-$DEVICE-$PORT_ARCH zypper -n --plus-repo $ANDROID_ROOT/droid-local-repo/$DEVICE install --allow-unsigned-rpm hybris-libsensorfw-qt5 mce-plugin-libhybris ngfd-plugin-native-vibrator pulseaudio-modules-droid qtscenegraph-adaptation
sb2 -t $VENDOR-$DEVICE-$PORT_ARCH -R -m sdk-install zypper in droid-config-$DEVICE ofono-configs-binder
sdk-assistant maintain $VENDOR-$DEVICE-$PORT_ARCH zypper -n --plus-repo $ANDROID_ROOT/droid-local-repo/$DEVICE install --allow-unsigned-rpm droid-config droid-config-preinit-plugins droid-config-pulseaudio-settings droid-config-sailfish qt5-qpa-hwcomposer-plugin
```

