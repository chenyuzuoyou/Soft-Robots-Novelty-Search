project( RandomSoftBots )
cmake_minimum_required( VERSION 2.6 )
set ( CMAKE_BUILD_TYPE Release )
add_definitions ( -Wall )
find_package ( Qt4 REQUIRED )
include ( ${QT_USE_FILE} )
include_directories (
        ${CMAKE_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR}
        ${QT_QTCORE_INCLUDE_DIR} ${QT_QTCORE_INCLUDE_DIR}
        $$PWD/../VoxSim/VoxBotCreator
        "../VoxSim/VoxBotCreator"
)

find_library(libVoxBotCreator "../VoxSim/build")

find_file(libVoxBotCreator libVoxBotCreator.so "../VoxSim/build")
if(NOT libVoxBotCreator)
  message(SEND_ERROR "Cannot find library libVoxBotCreator.so")
endif(NOT libVoxBotCreator)


set ( RandomVoxBotGenerator_SRCS
        RandomSoftBots.cpp
        )

add_executable ( RandomSoftBots ${RandomVoxBotGenerator_SRCS})
target_link_libraries ( RandomSoftBots  ${QT_QTCORE_LIBRARY} ${QT_QTCORE_LIBRARY} ${libVoxBotCreator})
