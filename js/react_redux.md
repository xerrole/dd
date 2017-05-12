# redux

redux的combineReducers()方法，其本质是合并所有reducers的各个case成为一个大的case。

当dispatch调用action的时候，使用action.type去顺序调用这些reducers，如果当前reducer中有匹配的case就进入处理，因此如果多个reducer中有相同的case的话，这些reducer中的case都会被处理。

dispatch的逻辑伪代码如下：

    for (var reducer in reducers) {
        for (var case in reducer.cases) {
            if (case.selector === action.type) {
                ... call case(action) ...
            }
        }
    }
