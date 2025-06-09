You want to reduce the number of features to be used by a classifier by maximizing the separation
between the classes, Try linear discriminant analysis (LDA) to project the features onto component axes that maximize the
separation of classes, We can use explained_variance_ratio_ to view the amount of variance explained by each
component. In our solution the single component explained over 99% of the variance, LDA is a classification that is also a popular technique for dimensionality reduction. LDA works
similarly to principal component analysis (PCA) in that it projects our feature space onto a lowerdimensional space. However, in PCA we were only interested in the component axes that maximize the
variance in the data, while in LDA we have the additional goal of maximizing the differences between
classes. In this pictured example, we have data comprising two target classes and two features. If we
project the data onto the y-axis, the two classes are not easily separable (i.e., they overlap), while if we
project the data onto the x-axis, we are left with a feature vector (i.e., we reduced our dimensionality by
one) that still preserves class separability. In the real world, of course, the relationship between the
classes will be more complex and the dimensionality will be higher, but the concept remains the same, In scikit-learn, LDA is implemented using LinearDiscriminantAnalysis, which includes a parameter,
n_components, indicating the number of features we want returned. To figure out what argument value
to use with n_components (e.g., how many parameters to keep), we can take advantage of the fact that
explained_variance_ratio_ tells us the variance explained by each outputted feature and is a sorted
array, Specifically, we can run LinearDiscriminantAnalysis with n_components set to None to return the
ratio of variance explained by every component feature, then calculate how many components are
required to get above some threshold of variance explained (often 0.95 or 0.99), 
