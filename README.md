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
                <li>固定11个水印，布局与示范图片完全一致</li>
                <li>高质量输出，仅当文件大于4MB时进行压缩</li>
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
                    <p class="img-title">加水印后</p>
                    <img id="watermarkImage" alt="加水印后图片">
                </div>
            </div>
            
            <div class="size-info" id="sizeInfo"></div>
            <div class="btn-group">
                <button class="btn btn-primary" id="downloadBtn">长按图片保存到手机相册</button>
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
        // 根据示范图片，水印颜色为浅灰色，透明度适中
        const WATERMARK_COLOR = 'rgba(153, 153, 153, 0.6)';
        // 根据示范图片，旋转角度为-45度
        const ROTATE_ANGLE = -45;
        // 最大文件大小限制为4MB
        const MAX_FILE_SIZE = 4 * 1024 * 1024;
        // 固定11个水印
        const WATERMARK_COUNT = 11;

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
                    
                    // 智能处理图片，仅当大于4MB时进行压缩
                    processImageSmart(imgSrc, img.naturalWidth, img.naturalHeight);
                    
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

        // 智能处理图片：仅当大于4MB时才压缩
        function processImageSmart(imgSrc, imgWidth, imgHeight) {
            const img = new Image();
            img.onload = function() {
                // 使用原图尺寸，保持最高质量
                let targetWidth = imgWidth;
                let targetHeight = imgHeight;
                
                // 设置高质量画布
                canvas.width = targetWidth;
                canvas.height = targetHeight;
                
                // 设置高质量渲染
                ctx.imageSmoothingEnabled = true;
                ctx.imageSmoothingQuality = 'high';
                
                // 清除画布并绘制原图
                ctx.clearRect(0, 0, targetWidth, targetHeight);
                ctx.drawImage(img, 0, 0, targetWidth, targetHeight);
                
                // 添加固定11个水印（示范图片布局）
                addOptimized11Watermarks(targetWidth, targetHeight);
                
                // 首先尝试最高质量输出（1.0）
                let quality = 1.0;
                let compressedDataUrl = canvas.toDataURL('image/jpeg', quality);
                let compressedSize = getDataUrlSize(compressedDataUrl);
                
                // 如果文件大于4MB，才进行压缩处理
                if (compressedSize > MAX_FILE_SIZE) {
                    // 逐步降低质量，直到文件小于4MB或达到最低质量0.85
                    while (compressedSize > MAX_FILE_SIZE && quality > 0.85) {
                        quality -= 0.05;
                        compressedDataUrl = canvas.toDataURL('image/jpeg', quality);
                        compressedSize = getDataUrlSize(compressedDataUrl);
                    }
                    
                    // 如果质量降到0.85还是大于4MB，考虑缩小尺寸（作为最后手段）
                    if (compressedSize > MAX_FILE_SIZE) {
                        // 计算需要缩小的比例
                        const sizeRatio = Math.sqrt(MAX_FILE_SIZE / compressedSize);
                        targetWidth = Math.max(1200, Math.round(targetWidth * sizeRatio));
                        targetHeight = Math.max(900, Math.round(targetHeight * sizeRatio));
                        
                        // 重新绘制
                        canvas.width = targetWidth;
                        canvas.height = targetHeight;
                        ctx.clearRect(0, 0, targetWidth, targetHeight);
                        ctx.drawImage(img, 0, 0, targetWidth, targetHeight);
                        addOptimized11Watermarks(targetWidth, targetHeight);
                        
                        // 使用较高质量0.9重新输出
                        compressedDataUrl = canvas.toDataURL('image/jpeg', 0.9);
                        compressedSize = getDataUrlSize(compressedDataUrl);
                    }
                }
                
                // 显示最终图片
                watermarkImage.src = compressedDataUrl;
                
                // 显示文件大小信息
                const originalSize = fileInput.files[0]?.size || 0;
                sizeInfo.textContent = `原文件大小: ${formatFileSize(originalSize)} | 输出文件大小: ${formatFileSize(compressedSize)}`;
                
                if (compressedSize > MAX_FILE_SIZE) {
                    sizeInfo.innerHTML += ' <span style="color:#e53935;">(文件较大，已尽力压缩)</span>';
                } else if (compressedSize === getDataUrlSize(canvas.toDataURL('image/jpeg', 1.0))) {
                    sizeInfo.innerHTML += ' <span style="color:#4CAF50;">(图片大于4兆会智能处理大小)</span>';
                } else {
                    sizeInfo.innerHTML += ' <span style="color:#4CAF50;">(已优化到4MB以内)</span>';
                }
            };
            img.src = imgSrc;
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

        // 计算智能字体大小
        function calculateFontSize(imgWidth, imgHeight) {
            const minDimension = Math.min(imgWidth, imgHeight);
            
            // 根据图片大小调整字体大小
            if (minDimension < 800) {
                return 42; // 小图片
            } else if (minDimension < 1600) {
                return 50; // 中等图片
            } else {
                return 58; // 大图片
            }
        }

        // 优化11个水印布局：确保不交叉重叠，角度与示范图一致
        function addOptimized11Watermarks(imgWidth, imgHeight) {
            const fontSize = calculateFontSize(imgWidth, imgHeight);
            
            // 设置字体样式（与示范图片一致）
            ctx.font = `bold ${fontSize}px SimHei, Microsoft YaHei, sans-serif`;
            ctx.fillStyle = WATERMARK_COLOR;
            ctx.textAlign = 'center';
            ctx.textBaseline = 'middle';
            
            // 计算旋转角度（与示范图一致）
            const rotateRadian = (ROTATE_ANGLE * Math.PI) / 180;
            
            // 计算文本宽度和高度
            const textWidth = ctx.measureText(WATERMARK_TEXT).width;
            const textHeight = fontSize;
            
            // 避免重叠：确保水印之间有足够间距
            const minSpacingX = textWidth * 1.5;
            const minSpacingY = textHeight * 3;
            
            // 优化后的11个水印位置（相对坐标，确保不重叠）
            // 这些位置根据示范图布局调整，确保水印不交叉
            const positions = [
                // 第一行：3个水印（顶部区域）
                { x: imgWidth * 0.15, y: imgHeight * 0.1 },
                { x: imgWidth * 0.5, y: imgHeight * 0.1 },
                { x: imgWidth * 0.85, y: imgHeight * 0.1 },
                
                // 第二行：2个水印（中上部，交错排列）
                { x: imgWidth * 0.3, y: imgHeight * 0.3 },
                { x: imgWidth * 0.7, y: imgHeight * 0.3 },
                
                // 第三行：3个水印（中部）
                { x: imgWidth * 0.15, y: imgHeight * 0.5 },
                { x: imgWidth * 0.5, y: imgHeight * 0.5 },
                { x: imgWidth * 0.85, y: imgHeight * 0.5 },
                
                // 第四行：2个水印（中下部，交错排列）
                { x: imgWidth * 0.3, y: imgHeight * 0.7 },
                { x: imgWidth * 0.7, y: imgHeight * 0.7 },
                
                // 第五行：1个水印（底部）
                { x: imgWidth * 0.5, y: imgHeight * 0.9 }
            ];
            
            // 确保正好11个水印
            const finalPositions = positions.slice(0, WATERMARK_COUNT);
            
            // 绘制所有水印
            for (const pos of finalPositions) {
                // 检查水印是否在图片范围内
                if (pos.x > 0 && pos.x < imgWidth && pos.y > 0 && pos.y < imgHeight) {
                    ctx.save();
                    ctx.translate(pos.x, pos.y);
                    ctx.rotate(rotateRadian);
                    ctx.fillText(WATERMARK_TEXT, 0, 0);
                    ctx.restore();
                }
            }
            
            // 不再添加额外的中心水印，确保总共11个
        }

        downloadBtn.addEventListener('click', () => {
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
    </script>
</body>
</html>
