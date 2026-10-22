# littlefs 构建入口（模块自带 glue）。
#
# 与 modules/littlefs/littlefs.clayer.yml 一致：lfs.c、lfs_util.c，
# include 路径为模块根（lfs.h 供 omni/subsys/fs/littlefs_arch.c 使用）。

add_library(omni_module_littlefs OBJECT
    "${OMNI_MODULE_LITTLEFS_SRC}/lfs.c"
    "${OMNI_MODULE_LITTLEFS_SRC}/lfs_util.c")

target_include_directories(omni_module_littlefs PUBLIC
    "${OMNI_MODULE_LITTLEFS_SRC}")
target_link_libraries(omni_module_littlefs PUBLIC
    omni::framework omni::config omni::hal)

omni_apply_arch(omni_module_littlefs)
omni_apply_warnings(omni_module_littlefs)
