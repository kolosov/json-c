set(jsontests_src parse_flags.c  test2.c test_case.c test_locale.c test_parse.c test_printbuf.c test_set_serializer.c test1.c test4.c test_cast.c test_null.c test_parse_int64.c testReplaceExisting.c )

#include_directories("${CMAKE_CURRENT_BINARY_DIR}")

foreach(test_prog_src ${jsontests_src})
  string( REPLACE ".c" "" test_prog ${test_prog_src} )
  message(${test_prog} " === " ${test_prog_src})
  add_executable(${test_prog} ${test_prog_src})
  target_link_libraries(${test_prog} libjson)
endforeach()
