
```CPP
// Logic to enable the Debug Layer if we are in Debug mode

	UINT createDeviceFlags = 0;
#if defined( DEBUG_MODE )
	createDeviceFlags |= D3D11_CREATE_DEVICE_DEBUG;
#endif
```

---

```CPP
D3D_FEATURE_LEVEL featureLevel;
```

---

```cpp
HRESULT hr = D3D11CreateDeviceAndSwapChain( 
	nullptr,                            // Use default graphics adapter
	D3D_DRIVER_TYPE_HARDWARE,           // Use hardware acceleration
	nullptr,                            // No software rasterizer
	createDeviceFlags,                  // Debug/Normal flags
	nullptr, 0,                         // Use default feature levels
	D3D11_SDK_VERSION,                  // Standard SDK version
	&sd,                                // The description we just filled
	&m_swapChain,                       // Output: Swap Chain
	&m_device,                          // Output: Device
	&featureLevel,                      // Output: Actual feature level
	&m_deviceContext                    // Output: Context
);
```