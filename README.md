# addShopCarAnimation
加入购物车动画
示例:

/// 点击事件
    cell.addToShoppingCar = ^(UIImageView *imageView){
        
        UICollectionViewCell * wCell = (UICollectionViewCell *)[collectionView cellForItemAtIndexPath:indexPath];
        CGRect rect = wCell.frame;
        
        /// 获取当前cell 相对于self.view 当前的坐标
        rect.origin.y          = rect.origin.y - collectionView.contentOffset.y;

        CGRect imageViewRect   = imageView.frame;
        imageViewRect.origin.x = rect.origin.x;
        imageViewRect.origin.y = rect.origin.y + imageViewRect.origin.y;

        [[PurchaseCarAnimationTool shareTool] startAnimationandView:imageView
                                                               rect:imageViewRect
                                                        finisnPoint:CGPointMake(ScreenWidth / 4 * 2.5, ScreenHeight - 49)
                                                        finishBlock:^(BOOL finish) {
                                                            
                                                            if ([self.tabBarController isKindOfClass:[CFTabBarController class]]) {
                                                                
                                                                CFTabBarController *tabBar = (CFTabBarController *)self.tabBarController;
                                                                
                                                                UIButton *tabbarBtn = tabBar.tabBarItemView.subviews[3];
                                                                
                                                                [PurchaseCarAnimationTool shakeAnimation:tabbarBtn];
                                                            }
                                                            
                                                        }];
    };
    
