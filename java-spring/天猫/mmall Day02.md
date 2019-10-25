# mmall 实战 Day02

@JsonIgnore（方法上）：使之不在json序列化结果中。

@JsonSerialize（include = JsonSerialize.Inclusion.NON_NULL）

> NON_NULL，如果是null对象，key也会消失
