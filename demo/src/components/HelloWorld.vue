<template>
	<div ref="video">
		<button style="width: 100px;height: 100px;position: fixed;z-index: 1;" @click="sendMessage('loginFuction','hello')">hello</button>
	</div>
</template>

<script>
export default {
	data() {
	  return {
			videoComponent:null
	  };
	},
  mounted() {
    this.videoInit();
  },
  methods: {
    videoInit() {
			this.videoComponent = document.createElement("video", { is: "peer-stream" });
      this.videoComponent.style.width = '1000px'
      this.videoComponent.style.height = '800px'
			this.videoComponent.style.backgroundRepeat='no-repeat'
			this.videoComponent.style.backgroundSize = 'cover';
			this.videoComponent.style.backgroundPosition = 'center';
			this.videoComponent.id = "http://127.0.0.1:88/package/WindowsNoEditor/px_test.exe"
			this.$refs.video.appendChild(this.videoComponent)
			//接收消息
			this.videoComponent.addEventListener("message",(e)=>{
				this.receiveMessage(e)
			})
    },
		sendMessage(funcName,info){
			let message = {
			    "command": "callUEFunc",
			    "ueFunction": funcName,
			    "jsonContent": info
			}
			this.videoComponent.emitMessage(JSON.stringify(message))
		},
		receiveMessage(message){
			let info = JSON.parse(message.detail)
			if(info.ueFunction in this){
				this[info.ueFunction](info.jsonContent)
			}
		},
		loginReturnFuction(res){
			alert(res)
		}
  }
};
</script>