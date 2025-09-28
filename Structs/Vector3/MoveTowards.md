moves a point towards a target position at a constant speed without overshooting

```CPP
transform.position = Vector3.MoveTowards(transform.position, target.position, speed * Time.deltaTime);
```