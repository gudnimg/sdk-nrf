#
# Copyright (c) 2020 Nordic Semiconductor
#
# SPDX-License-Identifier: LicenseRef-Nordic-5-Clause
#

zephyr_include_directories(include)

zephyr_library()

zephyr_library_sources(nrf_rpc_os.c)

zephyr_library_sources_ifdef(CONFIG_NRF_RPC_IPC_SERVICE nrf_rpc_ipc.c)

zephyr_library_sources_ifdef(CONFIG_NRF_RPC_SERIALIZE_API nrf_rpc_serialize.c)

zephyr_library_sources_ifdef(CONFIG_NRF_RPC_CALLBACK_PROXY nrf_rpc_cbkproxy.c)

zephyr_library_sources_ifdef(CONFIG_NRF_RPC_UART_TRANSPORT nrf_rpc_uart.c)

if(DEFINED CONFIG_NRF_RPC_DEV_INFO OR DEFINED CONFIG_NRF_RPC_CRASH_GEN)
  add_subdirectory(rpc_utils)
endif()
