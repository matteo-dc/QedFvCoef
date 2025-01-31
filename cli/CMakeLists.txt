file(DOWNLOAD https://raw.githubusercontent.com/aportelli/OptParser/main/OptParser.hpp 
  ${CMAKE_BINARY_DIR}/deps/include/OptParser.hpp)
add_library(optparser INTERFACE)
target_include_directories(optparser INTERFACE ${CMAKE_BINARY_DIR}/deps/include)

add_executable(qed-fv-coef-anglepoints anglepoints.cpp)
target_include_directories(qed-fv-coef-anglepoints PRIVATE ${PROJECT_SOURCE_DIR}/lib)
target_link_libraries(qed-fv-coef-anglepoints qedfv OpenMP::OpenMP_CXX optparser)
install(TARGETS qed-fv-coef-anglepoints RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

add_executable(qed-fv-coef coef.cpp)
target_include_directories(qed-fv-coef PRIVATE ${PROJECT_SOURCE_DIR}/lib)
target_link_libraries(qed-fv-coef qedfv OpenMP::OpenMP_CXX optparser)
install(TARGETS qed-fv-coef RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

add_executable(qed-fv-coef-spherescan sphere.cpp)
target_include_directories(qed-fv-coef-spherescan PRIVATE ${PROJECT_SOURCE_DIR}/lib)
target_link_libraries(qed-fv-coef-spherescan qedfv OpenMP::OpenMP_CXX optparser)
install(TARGETS qed-fv-coef-spherescan RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

add_executable(qed-fv-coef-sectionscan section.cpp)
target_include_directories(qed-fv-coef-sectionscan PRIVATE ${PROJECT_SOURCE_DIR}/lib)
target_link_libraries(qed-fv-coef-sectionscan qedfv OpenMP::OpenMP_CXX optparser)
install(TARGETS qed-fv-coef-sectionscan RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
