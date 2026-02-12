add_executable(engine main.cpp glad.c)

target_include_directories(engine PRIVATE include)
target_link_libraries(engine PRIVATE SDL3::SDL3)

add_custom_command(TARGET engine POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy -t $<TARGET_FILE_DIR:engine> $<TARGET_RUNTIME_DLLS:engine>
    COMMAND_EXPAND_LISTS
)