cmake_minimum_required(VERSION 3.13)
project(untitled1)



set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -lz")

add_executable(untitled1 main.cpp)



# Poco
set(POCO_PREFIX "/usr/local")
set(POCO_INCLUDE_DIR    "${POCO_PREFIX}/include/Poco")
set(POCO_LIB_DIR        "${POCO_PREFIX}/lib")
set(POCO_LIBS           "${POCO_LIB_DIR}/libPocoNet.so"
                        "${POCO_LIB_DIR}/libPocoUtil.so"
                        "${POCO_LIB_DIR}/libPocoFoundation.so")

target_include_directories(untitled1 PRIVATE "${POCO_INCLUDE_DIR}")
target_link_libraries(untitled1 "${POCO_LIBS}")

# Boost
set(BOOST_PREFIX "/usr/local")
set(BOOST_INCLUDE_DIR    "${BOOST_PREFIX}/include/boost")
set(BOOST_LIB_DIR        "${BOOST_PREFIX}/lib")
set(BOOST_LIBS           )

target_include_directories(untitled1 PRIVATE "${BOOST_INCLUDE_DIR}")
target_link_libraries(untitled1 "${BOOST_LIBS}")

# nghttp2
target_include_directories(untitled1 PRIVATE "/usr/local/include/nghttp2")
target_link_libraries(untitled1 "/usr/local/lib/libnghttp2_asio.so"
                                "/usr/local/lib/libnghttp2.so")

# pthread
target_link_libraries(untitled1 "pthread"
                                "ssl"
                                "crypto")