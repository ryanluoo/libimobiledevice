CMAKE_MINIMUM_REQUIRED(VERSION 3.2)

PROJECT(idevicetools)

INCLUDE_DIRECTORIES(
        .
        include
        /usr/local/include
)

SET(CMAKE_CXX_FLAGS "-DHAVE_CONFIG_H")
SET(CMAKE_C_FLAGS "-DHAVE_CONFIG_H")

SET(LIBS
        /usr/local/lib/libimobiledevice.a
        /usr/local/lib/libusbmuxd.dylib
        /usr/local/lib/libplist.dylib
        /usr/local/lib/libtasn1.dylib
        /usr/local/lib/libgcrypt.dylib
        /usr/local/lib/libgnutls.dylib
        /usr/local/lib/libgpg-error.dylib)

SET(SYSLOG_SRC tools/idevicesyslog.c)
ADD_EXECUTABLE(idevicesyslog ${SYSLOG_SRC})
TARGET_LINK_LIBRARIES(idevicesyslog ${LIBS})

SET(ID_SRC tools/idevice_id.c)
ADD_EXECUTABLE(idevice_id ${ID_SRC})
TARGET_LINK_LIBRARIES(idevice_id ${LIBS})
