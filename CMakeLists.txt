cmake_minimum_required(VERSION 2.8)
project(mediasegmenter)

find_package(PkgConfig REQUIRED)
pkg_check_modules(FFMPEG REQUIRED libavcodec libavformat libavutil)

set(mediasegmenter_source_files
    mediasegmenter.c
    segmenter.c
    log.c
    util.c
    )

include_directories(${FFMPEG_INCLUDE_DIRS})
link_directories(
    ${FFMPEG_LIBRARY_DIRS}
    )

add_executable(mediasegmenter
    ${mediasegmenter_source_files}
    )
target_link_libraries(mediasegmenter
    ${FFMPEG_LIBRARIES}
    pthread
    m
)
