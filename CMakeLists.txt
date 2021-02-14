cmake_minimum_required(VERSION 3.15)
project(AlpacaFarm)

find_package(PkgConfig REQUIRED)
pkg_check_modules(ALPACA REQUIRED alpaca)

add_executable(alpaca_farm main.cpp)
target_include_directories(alpaca_farm PUBLIC ${ALPACA_INCLUDE_DIRS})
target_link_libraries(alpaca_farm LINK_PUBLIC ${ALPACA_LIBRARIES})

include(GNUInstallDirs)
install(TARGETS alpaca_farm
	RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
	PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
