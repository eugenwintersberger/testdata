set(IMAGES primitive_types.png)

foreach(IMAGE ${IMAGES})
    configure_file(${IMAGE} ${IMAGE} COPYONLY)
endforeach()