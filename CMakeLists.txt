include(FetchContent)

FetchContent_Declare(
    doctest
    GIT_REPOSITORY https://github.com/doctest/doctest.git
    GIT_TAG v2.4.11
)
FetchContent_MakeAvailable(doctest)

add_executable(test_protocol test_protocol.cpp ../src/protocol.cpp)
target_include_directories(test_protocol PRIVATE ../include)
target_link_libraries(test_protocol PRIVATE doctest::doctest)
add_test(NAME test_protocol COMMAND test_protocol)

add_executable(test_thread_pool test_thread_pool.cpp ../src/thread_pool.cpp ../src/logger.cpp)
target_include_directories(test_thread_pool PRIVATE ../include)
target_link_libraries(test_thread_pool PRIVATE doctest::doctest Threads::Threads)
add_test(NAME test_thread_pool COMMAND test_thread_pool)