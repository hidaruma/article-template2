project (word-article-template2)
cmake_minimum_required (VERSION 2.8)

set(CMAKE_MODULE_PATH $(PROJECT_SOURCE_DIR)/cmake)

set(TEXFILES_PATH ../../texfiles)
set(ARTICLE_NAME main)
set(TEXFIES_PREFIX word)

find_package(LATEX REQUIRED)
find_package(Latexmk REQUIRED)

option(ENABLE_LUATEX "enable the use of luatex" OFF)
option(ENABLE_XETEX "enable the use of xetrex" OFF)

set(PAPER_NAME ${ARTICLE_NAME})
if(ENABLE_LUATEX)
  set(LATEXMK_FLAGS "-pdf")
elseif(ENABLE_XETEX)
  set(LATEXMK_FLAGS "-xelatex")
else()
  set(LATEXMK_FLAGS "")
endif()
set(TEXFILES ${TEXFILES_PREFIX}.cls)
set(TEXFILES_SRC ${TEXFILES_PREFIX}.dtx)

add_custom_command(
	OUTPUT ${TEXFILES}
	COMMAND make
	ARGS ${TEXFILES} -C ${TEXFILES_PATH}
	COMMAND cp
	ARGS -r ${TEXFILES_PATH}/${TEXFILES} ${PROJECT_SOURCE_DIR}
	DEPENDS
	  ${TEXFILES_PATH}/${TEXFILES_SRC}
)

add_custom_command(
	OUTPUT ${PAPER_NAME}.pdf
	COMMAND ${LATEXMK_EXECUTABLE}
	ARGS ${LATEXMK_FLAGS} ${PAPER_NAME}.tex
	DEPENDS
	  ${PAPER_NAME}.tex
	  ${ARTICLE_NAME}.tex
	  ${TEXFILES}
)

add_custom_target(main ALL echo
	DEPENDS ${ARTICLE_NAME}.pdf
)

add_custom_target(main-clean CLEAN echo
	COMMAND ${LATEXMK_EXECUTABLE}
	ARGS -C 
	COMMAND rm
	ARGS -r ${TEXFILES}
)