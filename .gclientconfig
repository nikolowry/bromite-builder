solutions = [{
    "url": "https://chromium.googlesource.com/chromium/src.git",
    "managed": False,
    "name": "src",
    "custom_deps": {
        "src/native_client": None,
        "src/third_party/gvr-android-sdk/src": None,
        "src/third_party/arcore-android-sdk/src": None
    },
    "custom_hooks": [{
        "name": "gvr_static_shim_android_arm",
        "condition": False
    }, {
        "name": "gvr_static_shim_android_arm64",
        "condition": False
    }, {
        "name": "gvr_static_shim_custom_libcxx_android_arm",
        "condition": False
    }, {
        "name": "gvr_static_shim_custom_libcxx_android_arm64",
        "condition": False
    }, {
        "name": "sdkextras",
        "condition": False
    }, {
        "name": "sysroot_x86",
        "condition": False
    }, {
        "name": "sysroot_x64",
        "condition": False
    }, {
        "name": "vr_controller_test_api",
        "condition": False
    }, {
        "name": "test_fonts",
        "condition": False
    }, {
        "name": "zucchini_testdata",
        "condition": False
    }],
    "custom_vars": {
        "checkout_instrumented_libraries": False,
        "checkout_nacl": False,
        "checkout_traffic_annotation_tools": False
    }
}]

target_os = ["android"]
