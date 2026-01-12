# useEffect

Owner: Edwin

- componentDidMount, componentDidUpdate, componentWillUnMount
- Closure
- Each time one of the dependencies changes, the effect will be executed again.
- Every state variable and prop used inside the effect mush be included in the dependency array
- clean up function

```jsx
useEffect(() => {
    let mounted = true;
    const controller = new AbortController();

    setError("");
    const fetchData = async () => {
      try {
        const res = await axios.get(url, { signal: controller.signal });
        if (res.status === 200 && mounted) {
          setData(res.data);
        }
      } catch (err) {
        const error = err as AxiosError;
        setError(error?.message);
      } finally {
        setIsLoading(false);
      }
    };

    fetchData();

    return () => {
      mounted = false;
      controller.abort();
    };
  }, [url]);
```