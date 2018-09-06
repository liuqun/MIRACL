cmake_minimum_required(VERSION 3.10)
project(miracl)

add_library(miracl STATIC "")

# for x64 bit only at the moment
# cp mirdef.h64 mirdef.h
# cp mrmuldv.g64 mrmuldv.c

target_sources(miracl PRIVATE
  "${CMAKE_CURRENT_LIST_DIR}/source/mrcore.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrarth0.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrarth1.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrarth2.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mralloc.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrsmall.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrio1.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrio2.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrgcd.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrjack.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrxgcd.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrarth3.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrbits.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrrand.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrprime.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrcrt.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrscrt.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrmonty.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrpower.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrsroot.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrcurve.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrfast.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrshs.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrshs256.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrshs512.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrsha3.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrfpe.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mraes.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrgcm.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrlucas.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrzzn2.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrzzn2b.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrzzn3.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrzzn4.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrecn2.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrstrong.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrbrick.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrebrick.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrec2m.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrgf2m.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrflash.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrfrnd.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrdouble.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrround.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrbuild.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrflsh1.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrpi.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrflsh2.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrflsh3.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrflsh4.c"
  "${CMAKE_CURRENT_LIST_DIR}/source/mrmuldv.c"
  )
include_directories("${CMAKE_CURRENT_LIST_DIR}/include/")

add_library(big STATIC "${CMAKE_CURRENT_LIST_DIR}/source/big.cpp")
add_library(zzn STATIC "${CMAKE_CURRENT_LIST_DIR}/source/zzn.cpp")
add_library(ec2 STATIC "${CMAKE_CURRENT_LIST_DIR}/source/ec2.cpp")
add_library(crt STATIC "${CMAKE_CURRENT_LIST_DIR}/source/crt.cpp")
add_library(ecn STATIC "${CMAKE_CURRENT_LIST_DIR}/source/ecn.cpp")
add_library(flash STATIC "${CMAKE_CURRENT_LIST_DIR}/source/flash.cpp")
add_library(polymod STATIC "${CMAKE_CURRENT_LIST_DIR}/source/curve/polymod.cpp")
add_library(poly STATIC "${CMAKE_CURRENT_LIST_DIR}/source/curve/poly.cpp")

add_executable(bmark "${CMAKE_CURRENT_LIST_DIR}/source/bmark.c")
target_link_libraries(bmark miracl)

add_executable(fact "${CMAKE_CURRENT_LIST_DIR}/source/fact.c")
target_link_libraries(fact miracl)

add_executable(mersenne "${CMAKE_CURRENT_LIST_DIR}/source/mersenne.cpp")
target_link_libraries(mersenne big miracl)

add_executable(brent "${CMAKE_CURRENT_LIST_DIR}/source/brent.cpp")
target_link_libraries(brent big zzn miracl)

add_executable(sample "${CMAKE_CURRENT_LIST_DIR}/source/sample.cpp")
target_link_libraries(sample flash miracl)

add_executable(ecsgen "${CMAKE_CURRENT_LIST_DIR}/source/ecsgen.cpp")
target_link_libraries(ecsgen ecn big miracl)

add_executable(ecsign "${CMAKE_CURRENT_LIST_DIR}/source/ecsign.cpp")
target_link_libraries(ecsign ecn big miracl)

add_executable(ecsver "${CMAKE_CURRENT_LIST_DIR}/source/ecsver.cpp")
target_link_libraries(ecsver ecn big miracl)

add_executable(pk-demo "${CMAKE_CURRENT_LIST_DIR}/source/pk-demo.cpp")
target_link_libraries(pk-demo ecn big miracl)

add_executable(schoof "${CMAKE_CURRENT_LIST_DIR}/source/curve/schoof.cpp")
target_link_libraries(schoof polymod poly ecn crt zzn big miracl)
