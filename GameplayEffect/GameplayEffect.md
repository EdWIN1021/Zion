#### Duration Policy
- Instant  (立即生效，一次性执行)
- Has Duration (生效一段时间，可设置秒数)
- Infinite (无限持续，直到被移除)

#### Period

`Period` 定义了效果多久触发一次，比如每秒伤害一次。

#### Components

- Require Tags to Apply/Continue This Effect (只有当目标拥有指定标签时，这个效果才能应用或持续存在)
	- Application Tag Requirements （效果能不能被“应用”）
	- Ongoing Tag Requirements （效果是否“持续”）
	- Removal Tag Requirements （效果是否“被移除”）