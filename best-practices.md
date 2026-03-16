# 最佳实践

## 代码清理

### 必须移除
- 所有 console.log 调试语句
- 注释掉的死代码
- 未使用的导入 (import)
- 未使用的变量和参数
- 空的备份文件 (*.bak, *.backup)

### 必须修复
- 变量拼写错误 (如 disFromMoouse → disFromMouse)
- 重复的 import 语句应合并
- 缺少默认值的 props 应添加空对象 {}

## 性能优化

### React
- useEffect 中的验证逻辑只执行一次
- useMemo/useCallback 正确使用
- 移除重复的事件监听器

### Node.js
- 文件操作使用 try-finally 确保 close()
- WebSocket 添加错误处理
- 添加输入 debounce

### Bash
- 添加 `set -u` 检测未定义变量
- 添加 `set -o pipefail` 检测管道错误
- 使用 local 声明局部变量

## 内存泄漏防护

### Electron
- ipcMain 监听器在组件卸载时移除
- beforeunload 事件清理

### 浏览器
- 移除重复的事件监听器
- dialog 事件监听器在使用后移除

## 代码风格

### TypeScript
- 导出接口以提升可复用性
- 修复类型别名拼写错误
- 接口属性添加类型

### API
- 修复 HTTP 状态码使用错误 (如 res.send(401).json())
- 替换废弃的 API (如 url.parse → new URL())
