# # This is the main binary. List your C files here.
# add_executable(hello_freertos
#     task_delay.c
#     )

# pico_set_program_name(hello_freertos "test")
# pico_set_program_version(hello_freertos "0.1")

# # Modify the below lines to enable/disable output over UART/USB.
# # These are mutually exclusive, only set one.
# pico_enable_stdio_uart(hello_freertos 0)
# pico_enable_stdio_usb(hello_freertos 1)

# # Add the libraries to the build
# target_link_libraries(hello_freertos PRIVATE
#   pico_stdlib
#   pico_multicore
#   pico_async_context_freertos
#   FreeRTOS-Kernel-Heap4
# )

# # The CYW43 is the Wifi/Bluetooth module. If the board is set to pico_w, this
# # variable will be set and the wireless libraries added.
# if(PICO_CYW43_SUPPORTED)
#     # For led support on pico_w
#     target_link_libraries(hello_freertos PRIVATE
#         pico_cyw43_arch_none
#     )
# endif()

# # Another pico macro which generates the uf2 file in addition to the elf
# pico_add_extra_outputs(hello_freertos)

# add_custom_target(flash picotool load -f $<TARGET_FILE:hello_freertos> DEPENDS hello_freertos)


# Ashoton's Cmakelists

add_compile_definitions(
    DELAY_MS=100
    IN_PIN=6
    OUT_PIN=0)

add_executable(task_delay task_delay.c)
pico_enable_stdio_uart(task_delay 0)
pico_enable_stdio_usb(task_delay 1)
target_link_libraries(task_delay PRIVATE
  pico_stdlib
  pico_multicore
  pico_async_context_freertos
  FreeRTOS-Kernel-Heap4
)
pico_add_extra_outputs(task_delay)
add_custom_target(flash_delay picotool load -f $<TARGET_FILE:task_delay> DEPENDS task_delay)


add_executable(timer timer.c)
pico_enable_stdio_uart(timer 0)
pico_enable_stdio_usb(timer 1)
target_link_libraries(timer PRIVATE pico_stdlib)
pico_add_extra_outputs(timer)
add_custom_target(flash_timer picotool load -f $<TARGET_FILE:timer> DEPENDS timer)


add_executable(sleep sleep.c)
pico_enable_stdio_uart(sleep 0)
pico_enable_stdio_usb(sleep 1)
target_link_libraries(sleep PRIVATE pico_stdlib)
pico_add_extra_outputs(sleep)
add_custom_target(flash_sleep picotool load -f $<TARGET_FILE:sleep> DEPENDS sleep)


# add_executable(irq gpio_interrupt.c)
# pico_enable_stdio_uart(irq 0)
# pico_enable_stdio_usb(irq 1)
# target_link_libraries(irq PRIVATE pico_stdlib)
# pico_add_extra_outputs(irq)
# add_custom_target(flash_irq picotool load -f $<TARGET_FILE:irq> DEPENDS irq)

# add_executable(rtc rtc.c)
# pico_enable_stdio_uart(rtc 0)
# pico_enable_stdio_usb(rtc 1)
# target_link_libraries(rtc PRIVATE pico_stdlib hardware_rtc pico_cyw43_arch_none)
# pico_add_extra_outputs(rtc)
# add_custom_target(flash_rtc picotool load -f $<TARGET_FILE:rtc> DEPENDS rtc)