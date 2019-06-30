# PHP的生命周期

### 模块初始化
- sapi_initialize_empty_request
  - 对sapi_globals中全局变量进行初始化

- sapi_activate
  - 初始化SG相关变量
  - 调用 activate 和 input_filter_init 函数，不同的SAPI可以自定义实现这些函数

- php_output_startup
  - 使用宏定义对 output_globals 进行初始化，output_globals对应的结构体为 zend_output_globals
  - 分别对 php_output_handler_aliases、php_output_handler_conflicts、php_output_handler_reverse_conflicts 这三个 HashTable 进行初始化
  - 将 php_output_stdout 赋值给 php_output_direct，php_output_stdout 函数的作用是调用 fwrite 将字符串输出到stdout中

- php_startup_ticks
  - 对PG(tick_functions) 进行初始化，PG宏对应的是 core_globals 全局变量

- gc_globals_ctor
  - 初始化垃圾回收器，分配 zend_gc_globals 内存

- zend_startup，启动Zend引擎
  - zend_cpu_startup
  - start_memory_manager
    - 初始化内存管理
  - virtual_cwd_startup
    - 初始化 cwd_globals 变量
  - zend_startup_strtod
  - zend_startup_extensions_mechanism
    - 启动扩展机制
  - 设置一些util函数句柄，zend_error_cb、zend_printf、zend_write等
  - 设置词法和语法解析的入口函数 compile_file 以及执行的入口函数 execute_ex
    - compile_file 是词法和语法解析的入口
    - execute_ex 是 opcodes 执行的入口
  - 设置垃圾回收函数句柄，gc_collect_cycles
  - zend_vm_init
    - 初始化Zend虚拟机的handler
  - 对CG(function_table)、CG(class_table)、CG(auto_globals)、以及EG(zend_contents)进行初始化
  - ini_scanner_globals_ctor
    - 对 ini_scanner_globals 进行初始化
  - php_scanner_globals_ctor
    - 对 language_scanner_globals 进行初始化，对应的宏是LANG_SCNG(v)
  - zend_set_default_compile_time_values
    - 设置编译时的一些值
  - 同时将 error_reporting 默认设置为 E_ALL & ~E_NOTICE
  - zend_interned_strings_init
    - 初始化内部字符串
  - zend_startup_builtin_functions
    - 注册Zend核心扩展，初始化内部函数
  - zend_register_standard_constants
    - 注册Zend定义的标准常量，比如 E_ERROR
  - zend_register_auto_global
    - 将 GLOBALS 添加到 CG(auto_globals) 中 
  - zend_ini_startup
    - 初始化与配置文件php.ini解析相关的变量

- zend_register_list_destructors_ex
  - 注册析构函数list

- php_binary_init
  - 获取PHP执行的二进制的路径