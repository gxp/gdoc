# swupdate

SWUpdate - Software Update for Embedded Systems

SWUpdate is a Linux Update agent with the goal to provide an efficient and safe way to update an embedded system. SWUpdate supports local and remote updates, multiple update strategies and it can be well integrated in the Yocto build system by adding the meta-swupdate layer.

https://github.com/sbabic/swupdate


# hawkBit

IoT. Update. Device.

https://github.com/eclipse/hawkbit

Eclipse hawkBit is an domain independent back end solution for rolling out software updates to constrained edge devices as well as more powerful controllers and gateways connected to IP based networking infrastructure.

Device Integration

hawkBit does not provide off the shelf clients for devices as part of the project. The long term goal is to provide an Eclipse hono integration which will provide connectivity through various IoT protocols and as a result allows a wide range of clients to connect to hawkBit. However, the hawkBit Direct Device Integration (API) API is HTTP/JSon based which should allow any update client to integrate quite easily.

There are clients outside of the Eclipse IoT eco system as well, e.g.:

    SWupdate which is a Linux Update agent with focus on a efficient and safe way to update embedded systems.
    rauc-hawkbit which is a python-based hawkBit client application and library for the RAUC update framework.

hawkBit是一个服务端解决方案，不提供设备端方案，但容易集成。
