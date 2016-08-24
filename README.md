# react-native-screen-adapter
A function is a perfect solution to React Native screen adaptation

##React Native屏幕适配

* 使用尺寸适配，拷贝ScreenAdapter文件夹下的Transform.js文件到自己项目下即可使用。
* 注意：需要根据自己的切图基准改动两个值，见下面函数说明。

##可用平台
* IOS
* Android

##使用方法
* 在style样式中
* 例如：设置View的高度为150px(切图上的px值)
```
//导入
import p from '../utils/Transform';

class ScreenAdapterExample extends Component {

    //构造函数
    constructor(props) {
        super(props);
        // 初始状态
        this.state = {
            ...
        }
    }

    render() {
        return (
            <View style={styles.container}>
            </View>
        );
    }
}

//样式中使用
const styles = StyleSheet.create({
    container: {
        ...
        height: p(132)
    }
});
```

* 参考文档详情查看[CSDN博客](http://blog.csdn.net/zhaoyw2008/article/details/46008513)
* React Native[自适应布局方案](https://segmentfault.com/a/1190000004878644)

##Transform.js解析

* photo
* code
```
function p(n) {
    const deviceWidth = Dimensions.get('window').width;
    return Math.round((n / 3) * (PixelRatio.getPixelSizeForLayoutSize(deviceWidth) / PixelRatio.get()) / 360);
}
```

##p函数说明
* n: UI給的切图上的px值，也就是像素值
* 3：设备的dpi，也就是设备的像素密度等级，固定值(UI切图基准设备的dpi)
* 360: 设备的宽逻辑尺寸(dp单位)，详情见上面的CSDN博客
![image](https://github.com/lan-xue-xing/react-native-screen-adapter/raw/master/ScreenAdapter/imgs/a.png)
![image](https://github.com/lan-xue-xing/react-native-screen-adapter/raw/master/ScreenAdapter/imgs/b.png)
![image](https://github.com/lan-xue-xing/react-native-screen-adapter/raw/master/ScreenAdapter/imgs/c.png)