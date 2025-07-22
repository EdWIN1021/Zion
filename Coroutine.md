**Coroutine（协程）** 它允执行到某一步，先停一下（比如等几帧、等几秒），然后继续执行后面的代码。
它非常适合处理**等待、延迟、动画过渡、特效播放等时间控制**逻辑。

```cpp
private float onDamageVfxDuration = .2f;
private Coroutine onDamageVfxCoroutine;
```

```cpp
if(onDamageVfxCoroutine != null)  
{  
    StopCoroutine(onDamageVfxCoroutine);  
}
```

```cpp
onDamageVfxCoroutine = StartCoroutine(OnDamageVfxCo());
```


```cpp
private IEnumerator OnDamageVfxCo()  
{  
	/* before */
    yield return new WaitForSeconds(onDamageVfxDuration);  
	/* after */
}
```