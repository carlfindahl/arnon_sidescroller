# Arnon Sidescroller
add_executable(${PROJECT_NAME} "")

# Set source files
target_sources(${PROJECT_NAME}
               PRIVATE
               # Project Specific Files
               ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/clock.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/clock.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/application.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/application.cpp

               # Game Logic
               ${CMAKE_CURRENT_SOURCE_DIR}/src/gameObject.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/gameObject.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/component.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/component.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/world.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/world.cpp

               # Event Management
               ${CMAKE_CURRENT_SOURCE_DIR}/src/slot.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/signal.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/delegate.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/delegateBind.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/inputManager.h

               # Scene Management
               ${CMAKE_CURRENT_SOURCE_DIR}/src/scene.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/scene.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/sceneManager.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/sceneManager.cpp

               # Specific Scenes
               ${CMAKE_CURRENT_SOURCE_DIR}/src/scene_mainMenu.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/scene_optionsMenu.h

               # Rendering
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shape2D.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shape2D.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shape2D_quad.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shape2D_quad.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shape2D_circle.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shape2D_circle.cpp

               # Logger
               ${CMAKE_CURRENT_SOURCE_DIR}/src/debug/asserts.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/debug/logger.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/debug/arnlog.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/debug/arnlog.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/debug/autoTimer.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/debug/autoTimer.cpp

               # GLFW Wrapping
               ${CMAKE_CURRENT_SOURCE_DIR}/src/window.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/window.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/glfwCallbacks.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/glfwCallbacks.cpp

               # OpenGL Wrapping
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/glCallbacks.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/glCallbacks.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/glCore45.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/glCore45.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/framebuffer.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/framebuffer.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/texture.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/texture.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/animationTexture.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/animationTexture.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/vertexArray.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/vertexArray.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/vertexBuffer.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/vertexBuffer.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/indexBuffer.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/indexBuffer.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shaderObject.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shaderObject.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shaderProgram.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/shaderProgram.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/stb_image.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/GL/stb_image.cpp

               #ImGui Built in source since that is what is recommended
               ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imconfig.h
               # ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imgui_internal.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imgui.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imgui.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imgui_draw.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imgui_demo.cpp
               ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imgui_glfw.h
               ${CMAKE_CURRENT_SOURCE_DIR}/src/imgui/imgui_glfw.cpp
               )

# Set include directories
target_include_directories(${PROJECT_NAME}
                           PRIVATE
                           ${CMAKE_CURRENT_SOURCE_DIR}/src
                           )

# Find Packages
find_package(glfw3 3.2 REQUIRED)
find_package(glm REQUIRED)
find_package(OpenGL REQUIRED)
find_package(fmt REQUIRED)

# Filesystem must be linked explicitly on Unix
if(UNIX)
   target_link_libraries(${PROJECT_NAME} stdc++fs)
endif()

# Link Libraries
target_link_libraries(${PROJECT_NAME}
                      glfw
                      glm
                      OpenGL::GL
                      fmt::fmt
                      )

# TODO: Define Install Targets Here
