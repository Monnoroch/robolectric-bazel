ANDROID_ALL_JARS = [
    "@org_robolectric_android_all_9_robolectric_4913185_2//jar",
    "@org_robolectric_android_all_8_1_0_robolectric_4611349//jar",
    "@org_robolectric_android_all_8_0_0_r4_robolectric_r1//jar",
    "@org_robolectric_android_all_7_1_0_r7_robolectric_r1//jar",
    "@org_robolectric_android_all_7_0_0_r1_robolectric_r1//jar",
    "@org_robolectric_android_all_6_0_1_r3_robolectric_r1//jar",
    "@org_robolectric_android_all_5_1_1_r9_robolectric_r2//jar",
    "@org_robolectric_android_all_5_0_2_r3_robolectric_r0//jar",
    "@org_robolectric_android_all_4_4_r1_robolectric_r2//jar",
    "@org_robolectric_android_all_4_3_r2_robolectric_r1//jar",
    "@org_robolectric_android_all_4_2_2_r1_2_robolectric_r1//jar",
    "@org_robolectric_android_all_4_1_2_r1_robolectric_r1//jar",
]

java_library(
    name = "robolectric",
    testonly = True,
    data = [":robolectric-deps.properties"],
    visibility = ["//visibility:public"],
    exports = [
        ":android-all-jars",
        ":robolectric-itself",
    ],
)

java_library(
    name = "robolectric-itself",
    testonly = True,
    visibility = ["//visibility:public"],
    exports = [
        "@backport_util_concurrent_backport_util_concurrent//jar",
        "@classworlds_classworlds//jar",
        "@com_almworks_sqlite4java_sqlite4java//jar",
        "@com_google_android_apps_common_testing_accessibility_framework_accessibility_test_framework//jar",
        "@com_google_guava_guava//jar",
        "@com_google_protobuf_protobuf_java//jar",
        "@com_ibm_icu_icu4j//jar",
        "@junit_junit//jar",
        "@nekohtml_nekohtml//jar",
        "@nekohtml_xercesMinimal//jar",
        "@org_apache_ant_ant//jar",
        "@org_apache_ant_ant_launcher//jar",
        "@org_apache_maven_maven_ant_tasks//jar",
        "@org_apache_maven_maven_artifact//jar",
        "@org_apache_maven_maven_artifact_manager//jar",
        "@org_apache_maven_maven_error_diagnostics//jar",
        "@org_apache_maven_maven_model//jar",
        "@org_apache_maven_maven_plugin_registry//jar",
        "@org_apache_maven_maven_profile//jar",
        "@org_apache_maven_maven_project//jar",
        "@org_apache_maven_maven_repository_metadata//jar",
        "@org_apache_maven_maven_settings//jar",
        "@org_apache_maven_wagon_wagon_file//jar",
        "@org_apache_maven_wagon_wagon_http_lightweight//jar",
        "@org_apache_maven_wagon_wagon_http_shared//jar",
        "@org_apache_maven_wagon_wagon_provider_api//jar",
        "@org_bouncycastle_bcprov_jdk15on//jar",
        "@org_codehaus_plexus_plexus_container_default//jar",
        "@org_codehaus_plexus_plexus_interpolation//jar",
        "@org_codehaus_plexus_plexus_utils//jar",
        "@org_hamcrest_hamcrest_core//jar",
        "@org_hamcrest_hamcrest_library//jar",
        "@org_ow2_asm_asm//jar",
        "@org_ow2_asm_asm_commons//jar",
        "@org_ow2_asm_asm_tree//jar",
        "@org_robolectric_annotations//jar",
        "@org_robolectric_junit//jar",
        "@org_robolectric_resources//jar",
        "@org_robolectric_robolectric//jar",
        "@org_robolectric_sandbox//jar",
        "@org_robolectric_shadowapi//jar",
        "@org_robolectric_shadows_framework//jar",
        "@org_robolectric_utils//jar",
        "@xpp3_xpp3_min//jar",
    ],
)

java_library(
    name = "android-all",
    testonly = True,
    srcs = [":robolectric-deps.properties"],
    exports = [":android-all-jars"],
)

java_library(
    name = "android-all-jars",
    testonly = True,
    exports = ANDROID_ALL_JARS,
)

filegroup(
    name = "android-all-jars-filegroup",
    testonly = True,
    srcs = ANDROID_ALL_JARS,
    visibility = ["//visibility:public"],
)

genrule(
    name = "properties",
    testonly = True,
    srcs = [":android-all-jars-filegroup"],
    outs = ["robolectric-deps.properties"],
    cmd = "$(location :gen-deps) $(locations :android-all-jars-filegroup) > $@",
    tools = [":gen-deps"],
)

py_binary(
    name = "gen-deps",
    testonly = True,
    srcs = ["gen-deps.py"],
)
