```CPP
// Output Merger / Bind the RTV to the Output Merger stage of the GPU
m_deviceContext->OMSetRenderTargets( 
	1,                                         // NumViews
	&m_mainRenderTargetView,
	nullptr 
);
```