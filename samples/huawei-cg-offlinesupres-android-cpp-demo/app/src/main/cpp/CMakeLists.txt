cmake_minimum_required(VERSION 3.4.1)

include_directories(
        ${CMAKE_SOURCE_DIR}/include
        ${CMAKE_SOURCE_DIR}/include/Utils
        #${CMAKE_SOURCE_DIR}/include/CGKit
        )

add_library(
        main-lib
        SHARED
        source/Utils/help.cpp
        source/glestest.cpp
        )

#ADD_LIBRARY(
#        cgkit
#        SHARED
#        IMPORTED)
#
#set_target_properties(cgkit
#        PROPERTIES IMPORTED_LOCATION
#        ${CMAKE_SOURCE_DIR}/../../../libs/${ANDROID_ABI}/libcgkit.so
#        )

#SET(
#        VULKAN_INCLUDE_DIR
#        "$ENV{VULKAN_SDK}/include")
#        #"${ANDROID_NDK}/sources/third_party/vulkan/src/include")
#
#include_directories(${VULKAN_INCLUDE_DIR})

#SET(
#        NATIVE_APP_GLUE_DIR
#        "${ANDROID_NDK}/sources/android/native_app_glue")
#
#FILE(
#        GLOB NATIVE_APP_GLUE_FILLES
#        "${NATIVE_APP_GLUE_DIR}/*.c"
#        "${NATIVE_APP_GLUE_DIR}/*.h")

#ADD_LIBRARY(native_app_glue
#        STATIC
#        ${NATIVE_APP_GLUE_FILLES})

#TARGET_INCLUDE_DIRECTORIES(
#        native_app_glue
#        PUBLIC
#        ${NATIVE_APP_GLUE_DIR})

find_library(
        log-lib
        log )

target_link_libraries(
        main-lib
        EGL
        GLESv3
        ${CMAKE_SOURCE_DIR}/../../../libs/${ANDROID_ABI}/libthirdpartyengine_plugin_offlineSupRes.so
        #${CMAKE_SOURCE_DIR}/../../../libs/${ANDROID_ABI}/libunity_plugin_offlineSupRes.so
        #${CMAKE_SOURCE_DIR}/../../../libs/${ANDROID_ABI}/libOSRPlugin.so
        #${CMAKE_SOURCE_DIR}/../../../libs/${ANDROID_ABI}/libPluginInterface.so
        android
        ${log-lib} )

#SET(
#        CMAKE_SHARED_LINKER_FLAGS
#        "${CMAKE_SHARED_LINKER_FLAGS} -u ANativeActivity_onCreate")
