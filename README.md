#   ZXingCode 二维码扫描

##  快速集成二维码扫描，生成二维码，可配置相册，闪光灯，相机可以调整焦距放大缩小，自定义扫描线颜色（ZXing 3.3.3）
[![](https://jitpack.io/v/maning0303/MNZXingCode.svg)](https://jitpack.io/#maning0303/MNZXingCode)

##  功能：
    1：生成二维码（带Logo）
    2：二维码扫描
    3：相册中选取图片识别
    4：开启闪光灯
    5: 相机可以调整焦距放大缩小

## 截图:
![image](https://github.com/maning0303/ZXingCodeDemo/blob/master/screenshots/mn_zxing_screenshot_001.png)
![image](https://github.com/maning0303/ZXingCodeDemo/blob/master/screenshots/mn_zxing_screenshot_002.jpeg)
![image](https://github.com/maning0303/ZXingCodeDemo/blob/master/screenshots/mn_zxing_screenshot_003.jpeg)
![image](https://github.com/maning0303/ZXingCodeDemo/blob/master/screenshots/mn_zxing_screenshot_004.jpeg)

## 如何添加
### Gradle添加：
#### 1.在Project的build.gradle中添加仓库地址

``` gradle
	allprojects {
		repositories {
			...
			maven { url "https://jitpack.io" }
		}
	}
```

#### 2.在Module目录下的build.gradle中添加依赖
``` gradle
	dependencies {
	     compile 'com.github.maning0303:MNZXingCode:V2.0.0'
	}
```

### 源码添加：
#### 直接拷贝整个module：libraryzxing，然后关联到你的项目就可以使用

## 使用方法:
###  进入需要提前申请相机权限；进入需要提前申请相机权限；进入需要提前申请相机权限；


``` java
        1：开始扫描：
            //默认扫描
            MNScanManager.startScan(this, new MNScanCallback() {
                   @Override
                   public void onActivityResult(int resultCode, Intent data) {
                    //TODO:
                    switch (resultCode) {
                        case MNScanManager.RESULT_SUCCESS:
                            String resultSuccess = data.getStringExtra(MNScanManager.INTENT_KEY_RESULT_SUCCESS);
                            break;
                        case MNScanManager.RESULT_FAIL:
                            String resultError = data.getStringExtra(MNScanManager.INTENT_KEY_RESULT_ERROR);
                            break;
                        case MNScanManager.RESULT_CANCLE:
                            showToast("取消扫码");
                            break;
                    }
                   }
            });
            
            
            //自定义扫描
            MNScanConfig scanConfig = new MNScanConfig.Builder()
                            //设置完成震动
                            .isShowVibrate(false)
                            //扫描完成声音
                            .isShowBeep(true)
                            //显示相册功能
                            .isShowPhotoAlbum(true)
                            //打开扫描页面的动画
                            .setActivityOpenAnime(R.anim.activity_anmie_in)
                            //退出扫描页面动画
                            .setActivityExitAnime(R.anim.activity_anmie_out)
                            //自定义文案
                            .setScanHintText("请将二维码放入框中...")
                            //扫描线的颜色
                            .setScanColor("#FFFF00")
                            //是否显示缩放控制器
                            .isShowZoomController(true)
                            //显示缩放控制器位置
                            .setZoomControllerLocation(MNScanConfig.ZoomControllerLocation.Bottom)
                            .builder();
            MNScanManager.startScan(this, scanConfig, new MNScanCallback() {
                @Override
                public void onActivityResult(int resultCode, Intent data) {
                    //TODO:
                    switch (resultCode) {
                        case MNScanManager.RESULT_SUCCESS:
                            String resultSuccess = data.getStringExtra(MNScanManager.INTENT_KEY_RESULT_SUCCESS);
                            break;
                        case MNScanManager.RESULT_FAIL:
                            String resultError = data.getStringExtra(MNScanManager.INTENT_KEY_RESULT_ERROR);
                            break;
                        case MNScanManager.RESULT_CANCLE:
                            showToast("取消扫码");
                            break;
                    }
                }
            });

        3：生成二维码：
        	Bitmap qrImage = ZXingUtils.createQRImage("xxxxxx");
        	Bitmap qrImage = ZXingUtils.createQRCodeWithLogo("xxxxxx", logoBitmap);
        	
        4：解析图片中的二维码：
        	String code = ZXingUtils.syncDecodeQRCode(String picturePath);
        	String code = ZXingUtils.syncDecodeQRCode(Bitmap bitmap);
```

## 版本记录：
    v2.0.0:
        1.添加缩放控制器，可以缩放相机焦距
        2.缩放控制器方向：左，右，下
        
    v1.1.9:
        1.添加退出动画配置
        2.修复activity动画黑色背景问题
        
    v1.1.8:
        1.扫描线动画处理
        2.优化UI
        
    v1.1.7:
        1.图片识别二维码对图片进行压缩处理，防止OOM
        2.优化界面显示
        
    v1.1.6:
        1.修复8.0-Only fullscreen opaque activities can request orientation错误
        2.优化启动退出动画


## 感谢：

[zxing](https://github.com/zxing/zxing)
[BGAQRCode-Android](https://github.com/bingoogolapple/BGAQRCode-Android)
感谢所有开源的人；



## 推荐:
Name | Describe |
--- | --- |
[GankMM](https://github.com/maning0303/GankMM) | （Material Design & MVP & Retrofit + OKHttp & RecyclerView ...）Gank.io Android客户端：每天一张美女图片，一个视频短片，若干Android，iOS等程序干货，周一到周五每天更新，数据全部由 干货集中营 提供,持续更新。 |
[MNUpdateAPK](https://github.com/maning0303/MNUpdateAPK) | Android APK 版本更新的下载和安装,适配7.0,简单方便。 |
[MNImageBrowser](https://github.com/maning0303/MNImageBrowser) | 交互特效的图片浏览框架,微信向下滑动动态关闭 |
[MNCalendar](https://github.com/maning0303/MNCalendar) | 简单的日历控件练习，水平方向日历支持手势滑动切换，跳转月份；垂直方向日历选取区间范围。 |
[MClearEditText](https://github.com/maning0303/MClearEditText) | 带有删除功能的EditText |
[MNCrashMonitor](https://github.com/maning0303/MNCrashMonitor) | Debug监听程序崩溃日志,展示崩溃日志列表，方便自己平时调试。 |
[MNProgressHUD](https://github.com/maning0303/MNProgressHUD) | MNProgressHUD是对常用的自定义弹框封装,加载ProgressDialog,状态显示的StatusDialog和自定义Toast,支持背景颜色,圆角,边框和文字的自定义。 |
[MNXUtilsDB](https://github.com/maning0303/MNXUtilsDB) | xUtils3 数据库模块单独抽取出来，方便使用。 |
[MNVideoPlayer](https://github.com/maning0303/MNVideoPlayer) | SurfaceView + MediaPlayer 实现的视频播放器，支持横竖屏切换，手势快进快退、调节音量，亮度等。------代码简单，新手可以看一看。 |
[MNZXingCode](https://github.com/maning0303/MNZXingCode) | 快速集成二维码扫描和生成二维码 |
[MNChangeSkin](https://github.com/maning0303/MNChangeSkin) | Android夜间模式，通过Theme实现 |
[SwitcherView](https://github.com/maning0303/SwitcherView) | 垂直滚动的广告栏文字展示。 |
[MNPasswordEditText](https://github.com/maning0303/MNPasswordEditText) | 类似微信支付宝的密码输入框。 |
[MNSwipeToLoadDemo](https://github.com/maning0303/MNSwipeToLoadDemo) | 利用SwipeToLoadLayout实现的各种下拉刷新效果（饿了吗，京东，百度外卖，美团外卖，天猫下拉刷新等）。 |

