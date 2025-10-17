## Starts Up

- When the engine first starts up, each subsystem must be configured and initialized in a specific order.
- Interdependencies between subsystems implicitly define the order in which they must be started.
- if subsystem B depends on subsystem A, then A will need to be started up before B can be initialized.

## Shut Down

- Occurs in the reverse order, so B would shut down first, followed by A.

---

## **Construction & Destruction Timing**

- Global and static objects are **constructed before** the program entry point (`main()` / `WinMain()` on Windows).
- Their **destructors run after** `main()` / `WinMain()` returns.

## **Unpredictable Order**

- **Construction order:** unpredictable.
- **Destruction order:** unpredictable.
- **Problem:** Makes it unsafe for initializing or shutting down subsystems that **depend on each other**.

Define explicit start-up and shut-down functions for each singleton manager class.

Constructor and destructor to do absolutely nothing.

```cpp
class RenderManager
{
public:
	RenderManager()
	{
		// do nothing
	}
	~RenderManager()
	{
		// do nothing
	}
	void startUp()
	{
	}
	void shutDown()
	{
	}
}
```