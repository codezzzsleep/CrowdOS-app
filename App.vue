<script>
	export default {
		onLaunch(options) {
		    const isLogged = uni.getStorageSync('currentUser'); // 从本地存储中获取登录状态
		    if (!isLogged) {
		      // 用户未登录，跳转到登录页
		      uni.reLaunch({
		        url: '/pages/page/login/login'
		      });
		    }
		  },
		globalData: {
			userInfo: null,
			tabBar: ['/pages/index', '/pages/task', '/pages/user'],
			homePage: '/pages/index',
			pages: ['/pages/index', '/pages/task', '/pages/user', '/pages/traffic', '/pages/route', '/pages/task', '/pages/page/publish', '/pages/page/taskList', '/pages/page/user', '/pages/login', '/pages/register']
		}
	};
</script>
<style lang="scss">
	@import 'common/diygw-ui/iconfont.scss';
	@import 'common/diygw-ui/animate.css';
	@import 'common/diygw-ui/index.scss';

	@import './uni_modules/diy-uview-ui/index.scss';
	@import 'common/diygw-ui/uview.scss';
</style>
