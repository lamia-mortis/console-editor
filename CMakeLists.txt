cmake_minimum_required (VERSION 3.11)
 
include(FetchContent)
set(FETCHCONTENT_UPDATES_DISCONNECTED TRUE)
FetchContent_Declare(ftxui
  GIT_REPOSITORY https://github.com/ArthurSonzogni/ftxui
  GIT_TAG v5.0.0 
)
FetchContent_Declare(pugixml
  GIT_REPOSITORY https://github.com/zeux/pugixml
  GIT_TAG v1.14
)
FetchContent_MakeAvailable(ftxui pugixml)
 
project(console-editor LANGUAGES CXX VERSION 1.0.0)

include_directories(include)

add_executable(
  console-editor 
  include/utils/fs.hpp
  include/utils/ui.hpp
  include/xml_processors/processor_base.hpp
  include/xml_processors/processor.hpp
  include/managers/fs_manager.hpp
  include/managers/render_manager.hpp
  src/main.cpp 
  src/utils/fs.cpp
  src/utils/ui.cpp
  src/xml_processors/processor.cpp
  src/xml_processors/recipes.cpp
  src/managers/fs_manager.cpp
  src/managers/render_manager.cpp
)
target_link_libraries(console-editor
  PRIVATE ftxui::screen
  PRIVATE ftxui::dom
  PRIVATE ftxui::component 
  pugixml
)
