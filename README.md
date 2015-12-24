# UICollectionView
Welcome to the UICollectionView wiki!
Demo中具有两种样式

第一种是CollectionView做的两级菜单，可以折叠第二级菜单

第二种是侧边栏菜单,具有多选功能,并可将数据持久化,在下次打开app后,保留用户的筛选条件.默认保存.

数据持久化使用NSCoding,若要关闭该项功能,可在AppDelegate里清除固化数据,

清除方法已经在工程中写出:

- (void)initFilterSetting:(BOOL)restore
{
    if (!restore) {
        CYLFilterParamsTool *filterParamsTool = [[CYLFilterParamsTool alloc] init];
        [NSKeyedArchiver archiveRootObject:filterParamsTool toFile:filterParamsTool.filename];
    }
}
用法如下

YES为保存,NO为不保存.

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    //...
    //设NO表示,每次启动程序,清除用户上次的筛选条件,不写该行,默认保存.
    [self initFilterSetting:NO];
    return YES;
}

转自https://github.com/ChenYilong/CollectionViewClassifyMenu
