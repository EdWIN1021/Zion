```cpp
private Coroutine imageEchoCo;
```

```cpp
if (imageEchoCo != null)
	StopCoroutine(imageEchoCo);
```

```cpp
 imageEchoCo = StartCoroutine(ImageEchoEffectCo(duration));
```



```cpp  
private IEnumerator ImageEchoEffectCo(float duration)
  {
      float timeTracker = 0;
      while (timeTracker < duration)
      {
          CreateImageEcho();

          yield return new WaitForSeconds(imageEchoInterval);
          timeTracker = timeTracker + imageEchoInterval;
      }
  }
```


```cpp
  private void CreateImageEcho()
  {
      GameObject imageEcho = Instantiate(imageEchoPrefab, transform.position, sr.transform.rotation);
      imageEcho.GetComponentInChildren<SpriteRenderer>().sprite = sr.sprite;
  }
```