<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>腾韵花园业主资料加水印工具</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Microsoft Yahei", "Helvetica Neue", Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #f5f5f5; 
            padding: 0;
            font-size: 14px;
            color: #333;
            line-height: 1.6;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        .page-container {
            width: 100%;
            max-width: 820px; 
            margin: 0 auto;
            padding: 30px 20px;
            flex: 1;
        }

        .header {
            text-align: center;
            padding: 10px 0 25px;
            position: relative;
        }

        .header h1 {
            color: #e53935; 
            font-weight: 700;
            font-size: 24px; 
            margin-bottom: 12px;
            letter-spacing: 1.2px;
        }

        .card {
            background-color: #ffffff;
            border-radius: 16px; 
            box-shadow: 0 1px 8px rgba(0, 0, 0, 0.04); 
            padding: 24px; 
            margin-bottom: 24px; 
            transition: all 0.3s ease-in-out; 
            border: 1px solid rgba(0, 0, 0, 0.02);
        }

        .card:hover {
            box-shadow: 0 2px 16px rgba(0, 0, 0, 0.06);
            transform: translateY(-1px);
        }

        .instruction-card .card-title {
            font-size: 17px;
            font-weight: 600;
            color: #222;
            margin-bottom: 16px;
            padding-left: 12px;
            border-left: 3px solid #2b85e4;
        }

        .instruction-list {
            list-style: none;
            padding-left: 0;
            color: #666;
        }

        .instruction-list li {
            margin-bottom: 10px;
            padding-left: 12px;
            position: relative;
            font-size: 14px;
        }

        .upload-card {
            text-align: center;
            padding: 50px 24px;
            border: 2px dashed #e8e8e8;
            cursor: pointer;
        }

        .upload-card .upload-icon {
            width: 70px;
            height: 70px;
            margin: 0 auto 20px;
            fill: #2b85e4;
            stroke: #2b85e4;
            opacity: 0.75;
            transition: all 0.3s ease-in-out;
        }

        .upload-card:hover .upload-icon {
            opacity: 1;
            transform: scale(1.08);
        }

        .upload-card .upload-text {
            color: #555;
            font-size: 16px;
            margin-bottom: 12px;
            font-weight: 500;
        }

        .upload-card .upload-tip {
            color: #999;
            font-size: 13px;
            line-height: 1.5;
        }

        #fileInput {
            display: none;
        }

        .preview-card {
            display: none;
        }

        .preview-card .card-title {
            font-size: 17px;
            font-weight: 600;
            color: #222;
            margin-bottom: 20px;
            padding-left: 12px;
            border-left: 3px solid #2b85e4;
        }

        .image-container {
            display: flex;
            flex-direction: column;
            gap: 24px;
            margin-bottom: 30px;
        }

        .image-box {
            width: 100%;
        }

        .image-box .img-title {
            font-size: 15px;
            color: #555;
            margin-bottom: 10px;
            font-weight: 500;
        }

        .image-box img {
            width: 100%;
            border-radius: 12px;
            box-shadow: 0 1px 6px rgba(0, 0, 0, 0.03);
            -webkit-touch-callout: default;
            transition: all 0.3s ease-in-out;
            border: 1px solid rgba(0, 0, 0, 0.02);
        }

        .image-box img:hover {
            box-shadow: 0 3px 12px rgba(0, 0, 0, 0.05);
        }

        .btn-group {
            display: flex;
            flex-direction: column;
            gap: 14px;
        }

        .btn {
            padding: 15px 24px;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            font-size: 15px;
            font-weight: 500;
            transition: all 0.3s ease-in-out;
            text-align: center;
        }

        .btn-primary {
            background: linear-gradient(135deg, #2b85e4, #1e74d4);
            color: #ffffff;
        }

        .btn-primary:hover {
            background: linear-gradient(135deg, #1e74d4, #1569c3);
            transform: translateY(-2px);
            box-shadow: 0 4px 16px rgba(43, 133, 228, 0.2);
        }

        .btn-default {
            background-color: #f8f8f8;
            color: #666;
            border: 1px solid rgba(0, 0, 0, 0.05);
        }

        .btn-default:hover {
            background-color: #f2f2f2;
            transform: translateY(-2px);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.03);
        }

        .footer {
            text-align: center;
            padding: 15px 0;
            color: #666;
            font-size: 13px;
            letter-spacing: 0.8px;
            border-top: 1px solid #eee;
            margin-top: 10px;
            width: 100%;
        }

        .footer .copyright {
            margin-bottom: 0;
            line-height: 1.8;
        }
        
        .size-info {
            text-align: center;
            color: #666;
            font-size: 13px;
            margin-top: 10px;
            padding: 8px;
            background-color: #f9f9f9;
            border-radius: 8px;
        }
    </style>
</head>
<body>
    <div class="page-container">
        <div class="header">
            <h1>腾韵花园业主资料加水印工具</h1>
        </div>

        <div class="card instruction-card">
            <div class="card-title">操作说明</div>
            <ul class="instruction-list">
                <li>点击上传区域选择需要加水印的图片</li>
                <li>智能布局10条水印，避免遮挡主要内容</li>
                <li>自动优化文件大小，确保清晰度</li>
                <li>长按水印图片可直接保存至手机相册</li>
            </ul>
        </div>

        <div class="card upload-card" id="uploadArea">
            <svg class="upload-icon" viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
                <polyline points="17 8 12 3 7 8"></polyline>
                <line x1="12" y1="3" x2="12" y2="15"></line>
            </svg>
            <p class="upload-text">点击此处上传图片</p>
            <p class="upload-tip">智能布局10条水印，避免遮挡主要内容，文件大小控制在1MB以内</p>
            <input type="file" id="fileInput" accept="image/*" multiple="false">
        </div>

        <div class="card preview-card" id="previewArea">
            <div class="card-title">预览效果</div>
            <div class="image-container">
                <div class="image-box">
                    <p class="img-title">原图</p>
                    <img id="originalImage" alt="原图">
                </div>
                <div class="image-box">
                    <p class="img-title">加水印后（智能布局，避免遮挡）</p>
                    <img id="watermarkImage" alt="加水印后图片">
                </div>
            </div>
            <div class="size-info" id="sizeInfo"></div>
            <div class="btn-group">
                <button class="btn btn-primary" id="downloadBtn">长按加水印后的图片保存至手机相册</button>
                <button class="btn btn-default" id="resetBtn">重新上传图片</button>
            </div>
        </div>
    </div>

    <div class="footer">
        <p class="copyright">Copyright © 2025 3栋-1903. All Rights Reserved.</p>
    </div>

    <script>
        const uploadArea = document.getElementById('uploadArea');
        const fileInput = document.getElementById('fileInput');
        const previewArea = document.getElementById('previewArea');
        const originalImage = document.getElementById('originalImage');
        const watermarkImage = document.getElementById('watermarkImage');
        const sizeInfo = document.getElementById('sizeInfo');
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        const downloadBtn = document.getElementById('downloadBtn');
        const resetBtn = document.getElementById('resetBtn');

        // 严格保留原水印文字内容，不做任何修改
        const WATERMARK_TEXT = '仅用于腾韵花园业委会成立备案，他用无效';
        // 浅灰色水印，与示例图片一致
        const WATERMARK_COLOR = 'rgba(153, 153, 153, 0.6)';
        // 精确匹配示例图片的旋转角度（-45度）
        const ROTATE_ANGLE = -45;
        // 固定水印数量
        const WATERMARK_COUNT = 10;
        // 最大文件大小限制（字节）
        const MAX_FILE_SIZE = 1024 * 1024; // 1MB

        // 智能计算水印参数，适应各种图片大小
        function calculateWatermarkParams(imgWidth, imgHeight) {
            // 基础参数（基于图片对角线长度）
            const diagonal = Math.sqrt(imgWidth * imgWidth + imgHeight * imgHeight);
            
            // 智能字体大小计算（基于图片尺寸）
            let fontSize;
            if (diagonal < 1000) {
                fontSize = Math.max(24, diagonal * 0.03);
            } else if (diagonal < 3000) {
                fontSize = Math.max(28, diagonal * 0.025);
            } else {
                fontSize = Math.max(32, diagonal * 0.02);
            }
            
            return {
                fontSize
            };
        }

        uploadArea.addEventListener('click', () => {
            fileInput.click();
        });

        fileInput.addEventListener('change', handleFileSelect);

        uploadArea.addEventListener('dragover', (e) => {
            e.preventDefault();
            uploadArea.style.borderColor = '#2b85e4';
            uploadArea.style.backgroundColor = '#f8f9fc';
        });

        uploadArea.addEventListener('dragleave', () => {
            uploadArea.style.borderColor = '#e8e8e8';
            uploadArea.style.backgroundColor = '#ffffff';
        });

        uploadArea.addEventListener('drop', (e) => {
            e.preventDefault();
            uploadArea.style.borderColor = '#e8e8e8';
            uploadArea.style.backgroundColor = '#ffffff';
            if (e.dataTransfer.files.length > 0) {
                fileInput.files = e.dataTransfer.files;
                handleFileSelect(e);
            }
        });

        // 智能压缩图片，确保文件大小在1MB以内
        function compressImage(dataUrl, imgWidth, imgHeight, callback) {
            const img = new Image();
            img.onload = function() {
                // 计算合适的压缩比例
                let targetWidth = imgWidth;
                let targetHeight = imgHeight;
                let quality = 0.9;
                
                // 如果图片太大，先缩小尺寸
                const maxDimension = 2000; // 最大边长限制
                if (Math.max(imgWidth, imgHeight) > maxDimension) {
                    const ratio = maxDimension / Math.max(imgWidth, imgHeight);
                    targetWidth = Math.round(imgWidth * ratio);
                    targetHeight = Math.round(imgHeight * ratio);
                }
                
                // 设置canvas尺寸
                canvas.width = targetWidth;
                canvas.height = targetHeight;
                ctx.clearRect(0, 0, targetWidth, targetHeight);
                ctx.drawImage(img, 0, 0, targetWidth, targetHeight);
                
                // 添加智能布局水印
                addSmartWatermark(targetWidth, targetHeight);
                
                // 尝试不同的质量参数，确保文件大小在1MB以内
                let compressedDataUrl = canvas.toDataURL('image/jpeg', quality);
                
                // 如果仍然太大，进一步降低质量
                while (getDataUrlSize(compressedDataUrl) > MAX_FILE_SIZE && quality > 0.3) {
                    quality -= 0.1;
                    compressedDataUrl = canvas.toDataURL('image/jpeg', quality);
                }
                
                // 如果还是太大，进一步缩小尺寸
                if (getDataUrlSize(compressedDataUrl) > MAX_FILE_SIZE) {
                    const sizeRatio = Math.sqrt(MAX_FILE_SIZE / getDataUrlSize(compressedDataUrl));
                    targetWidth = Math.round(targetWidth * sizeRatio);
                    targetHeight = Math.round(targetHeight * sizeRatio);
                    
                    canvas.width = targetWidth;
                    canvas.height = targetHeight;
                    ctx.clearRect(0, 0, targetWidth, targetHeight);
                    ctx.drawImage(img, 0, 0, targetWidth, targetHeight);
                    addSmartWatermark(targetWidth, targetHeight);
                    
                    compressedDataUrl = canvas.toDataURL('image/jpeg', 0.8);
                }
                
                callback(compressedDataUrl);
            };
            img.src = dataUrl;
        }

        // 计算DataURL的大小（字节）
        function getDataUrlSize(dataUrl) {
            const base64 = dataUrl.split(',')[1];
            return Math.round((base64.length * 3) / 4);
        }

        // 格式化文件大小显示
        function formatFileSize(bytes) {
            if (bytes < 1024) return bytes + ' B';
            else if (bytes < 1024 * 1024) return (bytes / 1024).toFixed(1) + ' KB';
            else return (bytes / (1024 * 1024)).toFixed(2) + ' MB';
        }

        function handleFileSelect(e) {
            const file = e.target.files[0] || e.dataTransfer.files[0];
            if (!file) return;

            // 显示文件大小信息
            sizeInfo.textContent = `原文件大小: ${formatFileSize(file.size)}`;
            
            const reader = new FileReader();
            reader.onload = function(event) {
                const imgSrc = event.target.result;
                const img = new Image();
                img.crossOrigin = 'anonymous';

                img.onload = function() {
                    originalImage.src = imgSrc;
                    
                    // 智能压缩并添加水印
                    compressImage(imgSrc, img.naturalWidth, img.naturalHeight, function(compressedImgSrc) {
                        watermarkImage.src = compressedImgSrc;
                        
                        // 显示压缩后的文件大小
                        const compressedSize = getDataUrlSize(compressedImgSrc);
                        sizeInfo.textContent += ` | 压缩后大小: ${formatFileSize(compressedSize)}`;
                        
                        if (compressedSize > MAX_FILE_SIZE) {
                            sizeInfo.innerHTML += ' <span style="color:#e53935;">(文件较大，建议使用更高压缩)</span>';
                        } else {
                            sizeInfo.innerHTML += ' <span style="color:#4CAF50;">(已优化到1MB以内)</span>';
                        }
                    });
                    
                    previewArea.style.display = 'block';
                    previewArea.scrollIntoView({ behavior: 'smooth', block: 'start' });
                };

                img.onerror = () => {
                    alert('图片加载失败，请更换一张图片重试');
                };
                img.src = imgSrc;
            };
            reader.readAsDataURL(file);
        }

        // 添加智能布局水印，避免遮挡主要内容
        function addSmartWatermark(imgWidth, imgHeight) {
            const params = calculateWatermarkParams(imgWidth, imgHeight);
            const { fontSize } = params;
            
            // 设置字体样式（黑体，加粗，精确匹配示例）
            ctx.font = `bold ${fontSize}px SimHei, Microsoft YaHei, sans-serif`;
            ctx.fillStyle = WATERMARK_COLOR;
            ctx.textAlign = 'center';
            ctx.textBaseline = 'middle';
            
            // 计算旋转角度
            const rotateRadian = (ROTATE_ANGLE * Math.PI) / 180;
            
            // 智能水印位置布局策略（避免遮挡主要内容）
            // 1. 边缘优先：主要分布在图片边缘区域
            // 2. 避免中心：尽量不遮挡图片中心主要内容
            // 3. 均匀分布：确保水印在图片四周都有分布
            
            // 定义智能水印位置
            const positions = [
                // 左上区域（边缘）
                { x: imgWidth * 0.15, y: imgHeight * 0.15 },
                // 右上区域（边缘）
                { x: imgWidth * 0.85, y: imgHeight * 0.15 },
                // 左下区域（边缘）
                { x: imgWidth * 0.15, y: imgHeight * 0.85 },
                // 右下区域（边缘）
                { x: imgWidth * 0.85, y: imgHeight * 0.85 },
                // 上边缘中间
                { x: imgWidth * 0.5, y: imgHeight * 0.1 },
                // 下边缘中间
                { x: imgWidth * 0.5, y: imgHeight * 0.9 },
                // 左边缘中间
                { x: imgWidth * 0.1, y: imgHeight * 0.5 },
                // 右边缘中间
                { x: imgWidth * 0.9, y: imgHeight * 0.5 },
                // 左上四分之一位置
                { x: imgWidth * 0.25, y: imgHeight * 0.25 },
                // 右下四分之一位置
                { x: imgWidth * 0.75, y: imgHeight * 0.75 }
            ];
            
            // 如果位置少于10个，补充一些边缘位置
            if (positions.length < WATERMARK_COUNT) {
                // 添加更多边缘位置
                positions.push(
                    { x: imgWidth * 0.25, y: imgHeight * 0.75 },
                    { x: imgWidth * 0.75, y: imgHeight * 0.25 }
                );
            }
            
            // 只取前10个位置
            const selectedPositions = positions.slice(0, WATERMARK_COUNT);
            
            // 绘制水印
            for (const pos of selectedPositions) {
                const { x, y } = pos;
                
                // 绘制水印
                ctx.save();
                ctx.translate(x, y);
                ctx.rotate(rotateRadian);
                ctx.fillText(WATERMARK_TEXT, 0, 0);
                ctx.restore();
            }
            
            // 可选：在图片四个角落添加小水印，进一步保护但不遮挡
            const cornerFontSize = fontSize * 0.7;
            ctx.font = `bold ${cornerFontSize}px SimHei, Microsoft YaHei, sans-serif`;
            
            // 四个角落的小水印
            const corners = [
                { x: imgWidth * 0.05, y: imgHeight * 0.05, angle: 0 },
                { x: imgWidth * 0.95, y: imgHeight * 0.05, angle: 0 },
                { x: imgWidth * 0.05, y: imgHeight * 0.95, angle: 0 },
                { x: imgWidth * 0.95, y: imgHeight * 0.95, angle: 0 }
            ];
            
            for (const corner of corners) {
                ctx.save();
                ctx.translate(corner.x, corner.y);
                ctx.rotate(corner.angle);
                ctx.fillText('腾韵花园', 0, 0);
                ctx.restore();
            }
        }

        downloadBtn.addEventListener('click', () => {
            alert('请直接长按预览区域内的"加水印后"图片，即可保存至手机相册！');
            const file = fileInput.files[0];
            if (!file) return;

            const originalName = file.name.split('.').slice(0, -1).join('.');
            const originalExt = 'jpg'; // 统一输出为jpg以控制大小
            const fileName = `${originalName}_水印_${new Date().getTime()}.${originalExt}`;

            const link = document.createElement('a');
            link.download = fileName;
            link.href = watermarkImage.src;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            URL.revokeObjectURL(link.href);
        });

        resetBtn.addEventListener('click', () => {
            if (confirm('确定要重新上传吗？当前内容将被清空！')) {
                fileInput.value = '';
                previewArea.style.display = 'none';
                originalImage.src = '';
                watermarkImage.src = '';
                sizeInfo.textContent = '';
                canvas.width = 0;
                canvas.height = 0;
                uploadArea.scrollIntoView({ behavior: 'smooth', block: 'start' });
            }
        });

        // 优化移动端体验
        document.addEventListener('touchstart', () => {}, { passive: true });
        
        // 防止长按菜单在移动端被屏蔽
        watermarkImage.style.webkitTouchCallout = 'default';
        watermarkImage.style.userSelect = 'auto';
        
        // 添加图片长按保存提示
        watermarkImage.addEventListener('contextmenu', (e) => {
            e.preventDefault();
            alert('请长按图片选择"保存图像"即可保存到手机相册');
        });
    </script>
</body>
</html>
