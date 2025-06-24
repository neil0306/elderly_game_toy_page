# 中老年平衡感训练游戏

一个专为中老年人设计的在线平衡感训练游戏，使用 MediaPipe 技术进行实时姿态检测，帮助用户改善平衡能力。

## 🎯 项目特色

- **👥 专为中老年人设计**：大字体、简洁界面、友好配色
- **🌍 多语言支持**：中文/英文切换
- **📱 移动端优化**：响应式设计，支持手机和平板
- **🎮 智能难度调节**：根据用户BMI和年龄自动推荐难度
- **🔒 隐私保护**：所有数据本地处理，不上传服务器
- **⚡ 实时分析**：使用 MediaPipe 进行实时姿态检测

## 🚀 功能特点

### 1. 用户友好设计
- 老年人友好的配色方案（深蓝色主题）
- 加粗字体，18px基础字体大小
- 简洁直观的界面设计
- 完整的免责声明

### 2. 智能游戏系统
- **三种难度等级**：简单、中等、困难
- **智能推荐**：基于BMI和年龄自动设置难度
- **实时评分**：基于姿态相似度计算分数
- **营养建议**：根据游戏表现提供个性化建议

### 3. 先进技术
- **MediaPipe 姿态检测**：实时分析用户动作
- **视频对比分析**：与标准动作进行实时对比
- **余弦相似度算法**：精确计算动作准确性
- **Canvas 可视化**：实时显示骨骼点和连接线

## 📋 使用流程

1. **免责声明**：阅读并同意使用条款
2. **信息输入**：输入年龄、性别、身高、体重
3. **难度选择**：系统自动推荐或手动选择难度
4. **开始游戏**：3秒倒计时后开始训练
5. **实时反馈**：查看动作分析和实时评分
6. **结果展示**：游戏结束后查看最终分数和营养建议

## 🛠 技术栈

- **前端**：HTML5, CSS3, JavaScript
- **AI技术**：Google MediaPipe
- **视频处理**：HTML5 Video API
- **图像处理**：Canvas API
- **摄像头访问**：WebRTC getUserMedia API

## 📁 文件结构

```
elderly_game_toy_page/
├── index.html              # 主游戏文件
├── easy.mp4               # 简单难度标准动作视频
├── medium.mp4             # 中等难度标准动作视频
├── hard.mp4               # 困难难度标准动作视频
├── README.md              # 项目说明文档
├── video-setup-guide.md   # 视频设置指南
├── deployment-guide.md    # 部署指南
└── todo.md               # 项目需求文档
```

## 🚀 快速开始

### 1. 克隆项目
```bash
git clone https://github.com/yourusername/elderly_game_toy_page.git
cd elderly_game_toy_page
```

### 2. 准备视频文件
根据 `video-setup-guide.md` 的说明准备三个难度的标准动作视频：
- `easy.mp4` - 简单难度
- `medium.mp4` - 中等难度  
- `hard.mp4` - 困难难度

### 3. 本地测试
由于需要摄像头权限，建议使用本地服务器：
```bash
# 使用 Python
python -m http.server 8000

# 或使用 Node.js
npx http-server
```

### 4. 部署到 GitHub Pages
参考 `deployment-guide.md` 进行部署。

## 🎯 BMI 难度推荐算法

```javascript
const bmi = weight / ((height / 100) ** 2);
let defaultDifficulty = 'medium';

if (age > 70 || bmi > 30) {
    defaultDifficulty = 'easy';    // 高龄或肥胖用户
} else if (bmi < 18.5 || (bmi >= 18.5 && bmi <= 24.9)) {
    defaultDifficulty = 'hard';    // 偏瘦或正常体重用户
}
```

## 📊 评分系统

### 计算方法
1. **姿态提取**：使用 MediaPipe 提取33个关键点
2. **关键点选择**：选择12个主要关键点进行比较
3. **距离计算**：计算用户姿态与标准姿态的欧几里得距离
4. **相似度转换**：`similarity = max(0, 100 - distance * 100)`
5. **平均得分**：所有帧的平均相似度作为最终得分

### 营养建议分级
- **80-100分**：动作标准程度高 - 维持性营养建议
- **60-79分**：动作标准程度中等 - 强化性营养建议  
- **0-59分**：动作标准程度低 - 补充性营养建议

## 🌐 浏览器支持

| 浏览器 | 最低版本 | 备注 |
|--------|----------|------|
| Chrome | 60+ | 推荐使用 |
| Firefox | 55+ | 完全支持 |
| Safari | 11+ | iOS 需要 12+ |
| Edge | 79+ | 基于 Chromium |

## 📱 移动端支持

- ✅ 响应式设计
- ✅ 触摸友好界面
- ✅ 移动端摄像头支持
- ✅ 竖屏/横屏适配

## 🔒 隐私保护

- 🚫 不收集个人数据
- 🚫 不上传视频内容
- 🚫 不保存用户信息
- ✅ 所有处理本地完成
- ✅ 符合 GDPR 要求

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

### 开发环境设置
1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/new-feature`
3. 提交更改：`git commit -am 'Add new feature'`
4. 推送分支：`git push origin feature/new-feature`
5. 提交 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙏 致谢

- [Google MediaPipe](https://mediapipe.dev/) - 提供强大的姿态检测技术
- [GitHub Pages](https://pages.github.com/) - 免费的静态网站托管服务

## 📞 联系方式

如有问题或建议，请通过以下方式联系：
- 提交 [GitHub Issue](https://github.com/yourusername/elderly_game_toy_page/issues)
- 发送邮件至：your.email@example.com

---

**⚠️ 重要提醒**：本网站提供的内容仅供参考，不构成专业医疗建议。使用前请咨询医生，运动时注意安全。
