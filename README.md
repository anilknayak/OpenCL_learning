# OpenCL
1. OpenCL host selects which devices should be placed in a context.
2. OpenCL host can dispatch the same kernel to multiple devices through their command queues
3. OpenCL devices contain multiple processing elements, and each element may process a subset of the input data
4. Host identifies the number of work items that should be generated to execute the kernel
5. Host creates a command queue for each device and enqueues commands. One type of command tells a device to execute a kernel.
6. OpenCL sets no constraints on how host applications distribute kernels to devices.
7. Host application's job involves creating kernels and deploying them to OpenCL-compliant devices such as GPUs, CPUs, or hybrid processors.

## The Five Data Structures
1. Device: A device receives kernels from the host (cl_device_id)
2. Kernel: Host application distributes kernels to devices (cl_kernel)
3. Program: Host selects kernels from a program (cl_program)
4. Command queue: Each device receives kernels through a command queue (cl_command_queue)
5. Context: Context allows devices to receive kernels and transfer data (cl_context)

## Function in OpenCL
1. clCreateCommandQueue
2. clGetDeviceInfo
3. clCreateKernel
4. clCreateContext

## OpenCL Kernels
To take advantage of these parallel-processing capabilities in code, an OpenCL developer needs to clearly understand two points:
1. The OpenCL Execution Model: Kernels are executed by one or more work-items. Work-items are collected into work-groups and each work-group executes on a compute unit.
2. The OpenCL Memory Model: Kernel data must be specifically placed in one of four address spaces — global memory, constant memory, local memory, or private memory. The location of the data determines how quickly it can be processed.

3. work-item has two IDs: a global ID and a local ID
4. global ID identifies the work-item among all other work-items executing the kernel
5. local ID identifies the work-item among other work-items in the work-group
6. Work-items in different work-groups may have the same local ID but they'll never have the same global ID


## OpenCL device model identifies four address spaces
1. Global memory: Stores data for the entire device.
2. Constant memory: Similar to global memory, but is read-only.
3. Local memory: Stores data for the work-items in a work-group.
4. Private memory: Stores data for an individual work-item.
