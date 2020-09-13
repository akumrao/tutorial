cmake_minimum_required(VERSION 3.7)

set(CWD ${CMAKE_CURRENT_LIST_DIR})

set(TEST_CC_FILTER ".*gunit.cc|.*/mock/.*|.*mock_.*|.*/mocks/.*|.*fake.*|.*/test/.*|.*/tests/.*|.*_test_.*|.*unittest.*|.*/end_to_end_tests/.*|.*_test.cc|.*_tests.cc|.*_integrationtest.cc|.*_perftest.cc|.*test_utils.cc|.*testutils.cc|.*testclient.cc|.*test.c")
set(OTHER_PLATFORM_CC_FILTER ".*_chromeos.cc|.*_freebsd.cc|.*_fuchsia.cc|.*/fuchsia/.*|.*_ios.cc|.*_ios.mm|.*/ios/.*|.*_mac.cc|.*_mac.mm|.*/mac/.*|.*_openbsd.cc|.*_win.cc|.*/win/.*|.*win32.*|.*/windows/.*|.*sse.cc|.*sse2.cc|.*_mips.cc|.*_mips.c")

# add at first, avoid header search path, definition chaos
add_subdirectory(third_party)

add_definitions(-DWEBRTC_POSIX=1, -DWEBRTC_LINUX=1, -DWEBRTC_ANDROID=1)
add_definitions(-DWEBRTC_ENABLE_PROTOBUF=1)
add_definitions(-DWEBRTC_INCLUDE_INTERNAL_AUDIO_DEVICE)
add_definitions(-DHAVE_PTHREAD -DHAVE_SCTP -DHAVE_WEBRTC_VIDEO -DHAVE_WEBRTC_VOICE)
add_definitions(-DUSE_BUILTIN_SW_CODECS)
add_definitions(-DENABLE_RTC_EVENT_LOG)
add_definitions(-DWEBRTC_NON_STATIC_TRACE_EVENT_HANDLERS=0)



add_definitions(-DWEBRTC_CODEC_ILBC -DWEBRTC_CODEC_OPUS -DWEBRTC_OPUS_SUPPORT_120MS_PTIME=1 -DWEBRTC_CODEC_ISAC -DWEBRTC_CODEC_RED)

add_definitions(-DWEBRTC_INTELLIGIBILITY_ENHANCER=0 -DWEBRTC_NS_FIXED)

add_definitions(-DWEBRTC_APM_DEBUG_DUMP=0)

set(CMAKE_BUILD_TYPE Debug)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g")

add_definitions(-DHAVE_NETINET_IN_H)

add_definitions(-DRTC_USE_H264)
add_definitions(-DWEBRTC_USE_H264)

include_directories(
    ${WEBRTC_REPO}

    ${WEBRTC_REPO}/${WEBRTC_BUILD_DIR}/gen

    ${WEBRTC_REPO}/third_party/abseil-cpp
    ${WEBRTC_REPO}/third_party/boringssl/src/include
    ${WEBRTC_REPO}/third_party/icu/source/common
    ${WEBRTC_REPO}/sdk/libs/ffmpeg/include
    ${WEBRTC_REPO}/third_party/jsoncpp/source/include
    ${WEBRTC_REPO}/third_party/libsrtp/config
    ${WEBRTC_REPO}/third_party/libsrtp/crypto/include
    ${WEBRTC_REPO}/third_party/libsrtp/include
    ${WEBRTC_REPO}/third_party/libyuv/include
    ${WEBRTC_REPO}/third_party/libvpx/source/libvpx
    ${WEBRTC_REPO}/third_party/opus/src/include
    ${WEBRTC_REPO}/third_party/protobuf/src
    ${WEBRTC_REPO}/third_party/openh264/src/include/
    ${WEBRTC_REPO}/third_party/openh264/src/
    ${WEBRTC_REPO}/third_party/usrsctp/usrsctplib
    ${webrtc_build_dir}/gen/sdk/android/generated_peerconnection_jni
    ${webrtc_build_dir}/gen/sdk/android/generated_logging_jni
    ${webrtc_build_dir}/gen/sdk/android/generated_native_api_jni/
#    ${WEBRTC_REPO}/third_party/libaom/source/libaom
)




file(GLOB_RECURSE src_api
    *.cpp
)

include_directories(apriltag1 PUBLIC /var/tmp/parent/third_party/del/include)

add_executable(eCAD main.cpp)

target_link_libraries(eCAD

del
 
)
